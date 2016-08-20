# 禁止颜色字面值

`no-color-literals` 规则会禁止在任何样式规则声明中使用颜色字面值和基础的颜色方法，变量和 maps/lists 除外。

被涉及到的颜色方法见下面所列出来的列表:
* `rgb`
* `rgba`
* `hsl`
* `hsla`

其他的颜色方法，比如 `adjust-color` 和 `mix` 也可能会被影响，除非他们所接收的原始颜色值是作为一个变量传进去。

## 可选的配置参数

* `allow-map-identifiers`: `true`/`false` (默认为 `true`)
* `allow-rgba`: `true`/`false` (默认为 `false`)
* `allow-variable-identifiers`: `true`/`false` (默认为 `true`)

## 例子

当启用时，而且默认的配置参数被使用，下面的写法是不被允许的。

```scss
.literal {
  color: mediumslateblue;
}

.linear-gradient-func {
  background: linear-gradient(top, #fff, white);
}

.box-shadow {
  box-shadow: 1px 1px black, 1px 1px black;
}

.background {
  background: 1px solid white;
}

.hex {
  color: #fff;
}

// rgb 方法直接作为方法参数传递
.adj {
  color: adjust-color(rgb(255, 0, 0), $blue: 5);
}

// hsl 方法直接作为方法参数传递
.scale {
  color: scale-color(hsl(120, 70%, 80%), $lightness: 50%);
}

// hsl 方法直接作为方法参数传递
.change {
  color: change-color(hsl(25, 100%, 80%), $lightness: 40%, $alpha: .8);
}

// 颜色十六进制值直接作为方法参数传递
.function {
  color: test(#fff);
}

// 颜色方法直接使用属性值作为参数
.rgb {
  color: rgb(255, 255, 255);
}

.rgba {
  color: rgba(255, 255, 255, .3);
}

.hsl {
  color: hsl(40, 50%, 50%);
}

.hsla {
  color: hsla(40, 50%, 50%, .3);
}

```

当启用时，而且默认的配置参数被使用，下面的写法是被允许的。

```scss
$literal: mediumslateblue;
$hexVar: #fff;
$rgb: rgb(255, 255, 255);
$rgba: rgba(255, 255, 255, .3);
$hsl: hsl(40, 50%, 50%);
$hsla: hsla(40, 50%, 50%, .3);

// 使用十六进制颜色值作为属性值
$colors: (
  red: #fff,
  blue : (
    orange: #fff
  )
);

// 使用颜色字面值作为变量标识符
$black: #000;

.literal {
  color: $literal;
}

.linear-gradient-func {
  background: linear-gradient(top, $hexVar, $literal);
}

.background {
  background: 1px solid $literal;
}

.hex {
  color: $hexVar;
}

.adj {
  color: adjust-color($off-red, $blue: 5);
}

.scale {
  color: scale-color($off-blue, $lightness: 50%);
}

.change {
  color: change-color($orange-extra, $lightness: 40%, $alpha: .8);
}

.function {
  color: test($hexVar);
}

.rgb {
  color: $rgb;
}

.rgba {
  color: $rgba;
}

.hsl {
  color: $hsl;
}

.hsla {
  color: $hsla;
}
```

---

## [allow-rgba: true]

当启用时，而且设置 `allow-rgba: true` ，下面的写法是被允许的:

```scss
// rgba 作为一个变量的值是没问题的
$rgba: rgba(255, 0, 0, .5);
$red: rgb(255, 255, 255,);

// rgba 方法可以直接使用如果他是一个变量的透明度
.color {
  color: rgba($red, .3);
}
```

另外，当启用时，而且设置为 `allow-rgba: true` ，下面的写法是不被允许的。
In addition, when enabled and `allow-rgba` is set to `true`, the following will be disallowed:

```scss
.color {
  // 一定要使用变量而不是直接的字面值
  color: rgba(0, 0, 0, .3);
  color: rgba(black, .3);
}
```

---

## [allow-variable-identifiers: false]

当启用时，而且设置 `allow-variable-identifiers: false` ，下面的写法是不被允许的。

```scss

// 变量使用一个颜色字面量作为一个标识符
$black: #000

// 变量使用一个颜色字面量作为一个标识符被作为参数传递给方法
.test {
  color: adjust-color($off-red, $blue: 5)
}

```

当启用时，而且设置 `allow-variable-identifiers: false` ，下面的写法是被允许的。

```scss

// 变量没有直接使用一个颜色字面量作为一个标识符
$primary-black: #000

```

---

## [allow-map-identifiers: false]

当启用时，而且设置 `allow-map-identifiers: false` ，下面的写法是不被允许的。

```scss

// map 标识符 red, blue, orange 和颜色字面值共享他们的名称，这是不应该使用的
// map identifiers red, blue and orange share their name with a
// color literal and therefore shouldn't be used
$colors: (
  red: #f00,
  blue: (
    orange: $orange
  )
)

```

当启用时，而且设置 `allow-map-identifiers: false` ，下面的写法是被允许的。

```scss

$colors: (
  primary-red: #f00,
  map-blue: (
    off-orange: $orange
  )
)

```
