# 禁止可合并的选择器

`no-mergeable-selectors` 规则会强制选择器不能被重复而且他们的属性应该被合并。你也可以传递一组你希望排除在这个规则之外的选择器白名单。

## 可选的配置参数

* `whitelist`: `[选择器组成的数组]` (默认为空数组 `[]`)

## 例子

当启用时，并且设置默认的参数，下面的写法会产生一个警告/错误:

```scss
.foo {
  content: 'bar';
}

// 重复的选择器
.foo {
  color: red;
}

h1,
h2,
h3 {
  content: '';
}

// 可以被合并的标识符
h1, h2, h3 {
  content: '';
}

.test {
  .bar {
    color: blue;
  }
}

// 2 个可合并的选择器 .test & .test .bar
.test {
  .bar {
    color: red;
  }
}
```

当设置参数为 `whitelist: ['div p', 'div a']` 时，下面的写法是被允许的而且不会再产生任何可合并的警告或错误:

```scss
div p {
  color: red;
}

// 不会因为可合并/重复而警告
div p {
  content: '';
}

div a {
  color: blue;
}

// 不会因为可合并/重复而警告
div a {
  content: '';
}
```

### Sass 语法用户注意

由于我们现在使用的 AST 版本的一个 bug ，gonzales-pe，我们现在不能强制这个规则在媒介查询条件中使用， SCSS 语法不会被影响，我们希望可以尽快改正它。
