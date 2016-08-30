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

* `@extend` 需要在样式属性声明前书写。

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

* `@extend` 需要在 Mixins (`@include`) 前书写。

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

* 只能继承占位符选择器的内容。

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

* `@include` 需要在样式属性声明前书写。

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

* 样式规则块（不包括注释）之间应该包含一个空白行，并且不允许单行的样式块出现。

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

* 每行只能声明一个样式属性。

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

* 选择器应该单独成行。

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

* 禁止使用颜色的字面值，建议使用十六进制的颜色值或者 `rgb` 。

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

* 

