# 链接的引号

`url-quotes` 规则会强制链接被包含在引号里面。

## 例子

当启用时，下面的写法是被允许的:

```scss
.foo {
  background-image: url('foo.png');
}

.qux {
  background-image: url('bar/' + $foo);
}

```

当启用时，下面的写法是不被允许的:

```scss
.bar {
  background-image: url(foo.png);
}

.norf {
  background-image: url(bar/ + $foo);
}

```
