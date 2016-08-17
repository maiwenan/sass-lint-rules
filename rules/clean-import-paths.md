# 简洁的文件导入路径

`clean-import-paths` 规则强制 `@import` 的路径是否需要使用开头处的下划线和（或者）文件名后缀。

## 可选的配置参数

* `leading-underscore`: `true`/`false` (默认为 `false`)
* `filename-extension`: `true`/`false` (默认为 `false`)

## 例子

### `leading-underscore`

设置 `leading-underscore: false` 时，下面的写法是被允许的。设置 `leading-underscore: true` 时，下面的写法是不被允许的。

```scss
@import '_foo';
@import '_bar/foo';
```

---

### `filename-extension`

设置 `filename-extension: false` 时，下面的写法是被允许的。设置 `filename-extension: true` 时，下面的写法是不被允许的。

```scss
@import 'foo';
@import 'bar/foo';
```

设置 `filename-extension: true` 时，下面的写法是被允许的。设置 `filename-extension: false` 时，下面的写法是不被允许的。

```scss
@import 'foo.scss';
@import 'bar/foo.scss';
```
