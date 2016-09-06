# sass 指南

用更合理的方式书写 sass

## 目录

* [继承](#继承)
* [Mixins](#Mixins)
* [行距](#行距)
* [禁止的做法](#禁止的做法)
* 嵌套
* 命名风格
* 样式规范
* 空格
* 结尾项


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

* 类选择器、方法、变量、 mixin 以及占位符命名使用 `hyphenatedlowercase` 风格

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

* 



















