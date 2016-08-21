# 禁止使用有协议的链接

`no-url-protocols` 规则会强制在链接中不能使用协议和域名。

## 例子

当启用时，下面的写法是被允许的:

```scss
.foo {
  background-image: url('/img/bar.png');
}

.foo {
  background-image: url('img/bar.png');
}

.foo {
  background-image: url('bar.png');
}
```

当启用时，下面的写法是不被允许的:

```scss
.foo {
  background-image: url('https://foo.com/img/bar.png');
}

.foo {
  background-image: url('http://foo.com/img/bar.png');
}

.foo {
  background-image: url('//foo.com/img/bar.png');
}
```
