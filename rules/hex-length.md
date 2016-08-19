# 十六进制值的长度

`hex-length` 规则会限制十六进制值的书写长度。

## 可选的配置参数

* `style`: `short`/`long` (默认为 `short`)

## 例子

设置为 `style: short` 时，下面的写法是被允许的。设置为 `style: long` 时，下面的写法是不被允许的。

```scss
$foo-color: #456;

.bar {
  background: linear-gradient(top, #3ff, #ddd);
}

.baz {
  color: #fff;
}
```

设置为 `style: long` 时，下面的写法是被允许的。设置为 `style: short` 时，下面的写法是不被允许的。

```scss
$foo-color: #445566;

.bar {
  background: linear-gradient(top, #33ffff, #dddddd);
}

.baz {
  color: #ffffff;
}
```

在上面两种情况下，下面的写法都是被允许的，因为下面的十六进制值不能被简写。

```scss
$quz-color: #abcdef;

.qux {
  color: #123456;
}
```
