# 十六进制符号

`hex-notation` 规则会强制十六进制值使用大写字母或者小写字母书写。

## 可选的配置参数

* `style`: `lowercase`/`uppercase` (默认为 `lowercase`)

## 例子

设置为 `style: lowercase` 是，下面的写法是被允许的。设置为 `style: uppercase` 时，下面的写法是不被允许的。

```scss
$foo-color: #fff;

.bar {
  background: linear-gradient(top, #cc2, #44d);
}

.baz {
  color: #12a;
}
```

设置为 `style: uppercase` 是，下面的写法是被允许的。设置为 `style: lowercase` 时，下面的写法是不被允许的。

```scss
$foo-color: #FFF;

.bar {
  background: linear-gradient(top, #CC2, #44D);
}

.baz {
  color: #12A;
}
```

在上面两种情况下，下面的写法都是被允许的，因为下面的十六进制值只包括数字

```scss
.qux {
  color: #123;
}
```
