# 缩进

`indentation` 规则会规定缩进的大小（tab 和空格），而且也会保证 tab 和空格不会混淆。

混合的 tab 和空格的警告检查会把你在配置文件中设置的是期待使用空格或者 tab 考虑进去。如果你的规则配置没有指定 tab 但是在文件的任何位置找到了 tab 符号，就会标记为一个警告。同样的，如果指定的是 tab ，那么对于任何的使用了空格的空白地方也会标记为一个警告。当然属性和值等之间的空格是会被忽略的。

## 可选的配置参数

* `size`: `number` or `'tab'` (默认为 `2` 个空格)

## 例子

当启用的时候（假设设置 `size: 2`），下面的写法是被允许的:

```scss
.foo {
  content: 'bar';

  .baz {
    content: 'qux';

    // Waldo
    &--waldo {
      content: 'alpha';
    }
  }
}
```

当启用的时候（假设设置 `size: 2`），下面的写法是不被允许的:

```scss
.foo {
content: 'bar';
   .baz {
  content: 'qux';
  // Waldo
      &--waldo {
        content: 'alpha';
      }
    }
}
```
