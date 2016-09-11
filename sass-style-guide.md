# sass 指南

用更合理的方式书写 sass

## 目录

* [继承](#继承)
* [Mixins](#Mixins)
* [行距](#行距)
* [禁止的做法](#禁止的做法)
* [嵌套](#嵌套)
* [命名风格](#命名风格)
* [样式规范](#样式规范)
* [空格](#空格)
* [结尾项](#结尾项)


## 继承

* `@extend` 需要在样式属性声明前书写

  ```
  // bad
  .foo {
    content: 'baz';
    @extend %bar;
  }
  ```

  ```
  // good
  .foo {
    @extend %bar;
    content: 'bar';
  }
  ```

* `@extend` 需要在 Mixins (`@include`) 前书写

  ```
  // bad
  .foo {
    @include bar;
    @extend %baz;
  }
  ```

  ```
  // good
  .foo {
    @extend baz;
    @include bar;
  }
  ```

* 只能继承占位符选择器的内容

  ```
  // bad
  .foo {
    @extend: .bar;
  }
  ```

  ```
  // good
  .foo {
    @extend %bar;
  }
  ```


## Mixins

* `@include` 需要在样式属性声明前书写

  ```
  // bad
  .foo {
    content: 'baz';
    @include bar;
  }
  ```

  ```
  // good
  .foo {
    @include bar;
    content: 'bar';
  }
  ```


## 行距

* 样式规则块（不包括注释）之间应该包含一个空白行，并且不允许单行的样式块出现

  ```
  // bad
  .foo {
    dispaly: block;
  }
  .bar {
    dispaly: flex;
  }

  // bad
  .foo { width: 100px; }
  ```

  ```
  // good
  .foo {
    dispaly: block;
  }

  .bar {
    dispaly: flex;
  }

  // good
  .foo {
    width: 100px;
  }
  ```

* 每行只能声明一个样式属性

  ```
  // bad
  .foo {
    dispaly: block; width: 100px;
  }
  ```

  ```
  // good
  .foo {
    dispaly: block;
    width: 100px;
  }
  ```

* 选择器应该单独成行

  ```
  // bad
  .foo, .bar {
    width: 100px;
  }
  ```

  ```
  // good
  .foo,
  .bar {
    width: 100px;
  }
  ```


## 禁止的做法

* 禁止使用颜色的字面值，建议使用十六进制的颜色值或者 `rgb` 

  ```
  // bad
  .foo {
    color: red;
  }
  ```

  ```
  // good
  .foo {
    color: #f00;
  }
  ```

* 禁止使用 `css` 的注释，建议使用 `sass` 的单行注释或者 `Bang` 注释

```scss

// 这是一个好的注释
/*!
 * 这是一个好的 Bang 注释
 **/


 /*
 * 这个多行注释是不好的
 */
```

* 禁止使用 `@debug` 表达式

```scss
// bad
@debug 'foo';
```

* 同一个样式块內不允许出现相同的 `css` 属性声明

```scss
// bad
.foo {
  margin: 0 0 15px;
  margin: 0;
}
```

* 禁止出现空白的样式规则集

```
//bad
.foo {
  
}
```

* 禁止使用 `ID` 选择器

```
//bad
#foo {
  
}
```

* 禁止使用 `important` 声明

```
//bad
.foo {
  width: 100px; !important;
}

// good
.foo {
  width: 100px;
}
```

* 禁止使用非法的十六进制

```
// bad
.foo {
  color: #frg;
}

// good
.foo {
  color: #f00;
}
```

* 禁止出现重复的选择器

```
// bad
.foo {
  .bar {
    color: #ff0;
  }
}
.foo {
  .bar {
    width: 100px;
  }
}

// good
.foo {
  .bar {
    width: 100px;
    color: #ff0;
  }
}
```

* 禁止拼写错误的属性及未知的属性，`touch-callout` `overflow-scrolling` 等除外

```
// bad
.foo {
  borders: 0;
}

// good
.foo {
  border: 0;
}
```

* 禁止行尾出现空格

```
// bad
.foo {
  margin: 1.5rem;\s
}

// good
.foo {
  margin: 1.5rem;
}
```

* 禁止小数点末位出现 0

```
// bad
.foo {
  width: 12.10%;
}

// good
.foo {
  width: 12.1%;
}
```

* 禁止 `transition` 属性使用 `all` 作为值

```scss
// bad
.foo {
  transition: all 2s;
}

// good
.foo {
  transition: color 2s;
}
```

* 禁止外链资源（图片，字体等）出现协议名称

```
// bad
.foo {
  background-image: url(https://foo.com/logg.png);
}

// good
.foo {
  background-image: url(./logg.png);
}
```

* 禁止在属性前添加浏览器前缀，`-webkit-` 除外，原因：适应部分还不会自动加前缀的属性，如: -webkit-tap-highlight-color

```
// bad
.foo {
  -moz-transition: none;
}

// good
.foo {
  transition: none;
}
```

* 禁止警告表达式

```
// bad
@warn 'foo';
```


## 嵌套

* 使用属性选择器时，需要使用嵌套的写法

```
// bad
input[class^="foo-"] {
  width: 100px;
}

// good
input {
  &[class^="foo] {
    width: 100px;
  }
}
```

* 使用多个元素选择器时，需要使用嵌套的写法

```
// bad
div a {
  dispaly: block;
}

// good
div {
  a {
    dispaly: block;
  }
}
```

* 使用伪元素或者伪类选择器时，需要使用嵌套的写法

```
// bad
.foo:before {
  dispaly: block;
}

// good
.foo {
  &:before {
    dispaly: block;
  }
}
```


## 命名风格

* 类选择器、方法、变量、 mixin 以及占位符命名使用 `hyphenatedlowercase` 风格，即多个分词使用破折号分隔

```
// bad
.foo_bar,
.FOO-BAR {
  width: 100px;
}

// good
.foo-bar {
  width: 100px;
}

// bad
@function hyphenated_lowercase() {
  @return "foo";
}
@function HYPHENATED-UPPERCASE() {
  @return "foo";
}

// good
@function hyphenated-lowercase() {
  @return "foo";
}

// bad
$min_height: 10;
$MIN-HEIGHT: 10;

// good
$min-height: 10;

// bad
%hyphenated_lowercase {
  content: '';
}
%HYPHENATED-UPPERCASE {
  content: '';
}

// good
%hyphenated-lowercase {
  content: '';
}
```


## 样式规范

* 属性选择器中的属性值需要使用引号包含起来

```
// bad
span[class^=main] {
  background-color: #ff0;
}

// good
span[class^='main'] {
  background-color: #ff0;
}
```

* 当元素的边框需要设置为 0 时，建议直接设置为 `0` ，不要设置为 `none`

```
// bad
.foo {
  border: none;
}

// good
.foo {
  border: 0;
}
```

* 使用大括号时，开括号应该在选择器、方法或者 mixin 等的后面，收括号应该单独成行；如果样式规则只声明了一个属性也需要这样做。

```
// bad
.foo
{
  width: 100px;
}
@function foo()
{
  width: 100px;
}
@mixin foo
{
  width: 100px;
}
.foo { color: #fff; }

// good
.foo {
  width: 100px;
}
@function foo() {
  width: 100px;
}
@mixin foo {
  width: 100px;
}
```

* `@import` 的路径不要使用开头处的下划线和（或者）文件名后缀

```
// bad
@import "foo.scss";
@import "_bar";

// good
@import "foo";
@import "bar";
```

* 当声明或者调用一个 `mixin` 的时候，如果没有定义任何参数或者没有使用任何参数，就不需要使用括号

```
// bad
@mixin foo() {
  width: 100px;
}
@include foo();

// good
@mixin foo {
  width: 100px;
}
@include foo;
```

* 使用十六进制的值时，能简写的一定要简写

```
// bad
.foo {
  color: #ffffff;
}

// good
.foo {
  color: #fff;
}
```

* 缩进的地方统一使用 2 个空格

```
// bad
.foo {
   width: 100px;
}
.bar {
    color: #f00;
}

// good
.foo {
  width: 100px;
}
.bar {
  color: #f00;
}
```

* 当属性的值包含数字时，如果整数位是 0 ，小数点不为 0 的，整数位的 0 都不要写

```
// bad
.foo {
  margin-left: 0.6rem;
}

// good
.foo {
  margin-left: .6rem;
}
```

* 选择器的最大嵌套层数不能超过 3 层

```
// bad
.foo {
  .bar {
    .content {
      .title {
        width: 100px;
      }
    }
  }
}

// good
.foo {
  .title {
    width: 100px;
  }
}
.foo {
  .bar {
    .title {
      width: 100px;
    }
  }
}
```

* 规则属性的声明顺序需要遵循 [`recess`](https://github.com/sasstools/sass-lint/blob/develop/lib/config/property-sort-orders/recess.yml) 风格

* 需要使用引号的字符串都要使用单引号 (`'`)

```
// bad
.foo[^class="bar"] {
  width: 100px;
}
.bar {
  content: "12";
}

// good
.foo[^class='bar'] {
  width: 100px;
}
.bar {
  content: '12';
}
```

* 多个值的属性需要使用简洁模式

```
// bad
margin: 1px 1px 1px 1px;

// good
margin: 1px;
```

* 当属性的值使用到路径或者网址时，其值不要使用引号包含起来

```
// bad
.foo {
  background-image: url('./images/logo.png');
}

// good
.foo {
  background-image: url(./images/logo.png);
}
```

* 属性值的大小为 `0` 的不要使用单位

```
// bad
.foo {
  margin-left: 0px;
}

// good
.foo {
  margin-left: 0;
}
```


## 空格

* 括号 (`()`) 里面第一个元素的前面和最后一个元素的后面都不要使用一个空格进行分隔

```
// bad
@function foo( $bar ) {
  @return $bar;
}

@mixin bar($baz ) {
  content: $baz;
}

.foo {
  @include bar( 'Hello' );
  content: foo( 'bar');
  width: calc( 100% - 10px);
}

// good
@function foo($bar) {
  @return $bar;
}

@mixin bar($baz) {
  content: $baz;
}

.foo {
  @include bar('Hello');
  content: foo('bar');
  width: calc(100% - 10px);
}
```

* 操作符的前面和后面都要使用一个空格和其前面或者后面的内容进行分隔；操作符 : `+`, `-`, `/`, `*`, `%`, `<`, `>` `==`, `!=`, `<=` and `>=`

```
// bad
.foo {
  margin: 5px +15px;
}
$foo: 1+1;
$bar: 1+ 1;

// good
.foo {
  margin: 5px + 15px;
}
$foo: 1 + 1;
$bar: 1 + 1;
```

* 叹号 (`!`) 不要使用一个空格和其后面的内容进行分隔

```scss
// bad
.foo {
  content: 'bar' ! important;
}

// good
.foo {
  content: 'bar' !important;
}
```

* 冒号 (`:`) 、逗号 (`,`) 等要使用一个空格和其后面的内容进行分隔

```scss
// bad
.foo {
  content:'bar';
}
.foo {
  @include baz('foo','bar');

  box-shadow: 1px 1px black,1px 1px black;
}

// good
.foo {
  content: 'bar';
}
.foo {
  @include baz('foo', 'bar');

  box-shadow: 1px 1px black, 1px 1px black;
}
```

* 叹号 (`!`) 、开大括号 (`{`) 等要使用一个空格和其前面的内容进行分隔

```scss
// bad
.foo {
  content: 'bar'!important;
}
.bar{
  width: 100px;
}

// good
.foo {
  content: 'bar' !important;
}
.bar {
  100px;
}

```

* 冒号 (`:`) 不要使用一个空格和其前面的内容进行分隔

```scss
// bad
.foo {
  content : 'bar';
}

// good
.foo {
  content: 'bar';
}
```


## 结尾项

* 文件应该要以新的一行结尾

```scss
// bad
.foo {
  content: 'bar';
}
// 该注释下没有新的空行
// good
.foo {
  content: 'bar';
}
// 该注释下有新的空行

```

* 在一个样式块中样式声明的最后要包含一个分号 (`;`) (`.sass` 语法除外)

```
// bad
.foo {
  width: 100px
}

// good
.foo {
  width: 100px;
}
```
