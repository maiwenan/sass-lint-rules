# 禁止拼写错误的属性

`no-misspelled-properties` 规则会强制书写正确的 CSS 属性，而且禁止使用未知的 CSS 属性。

## 可选的配置参数

* `extra-properties`: `[一组额外的不进行检测的属性]` (默认为空数组 `[]`).

## 例子

当启用时，下面的写法是不被允许的:

```scss

// 不正确的拼写
.foo {
  borders: 0;
}

// 未知的属性
.bar {
  border-right-left: 0;
}

// 不正确的拼写
.baz {
  -webkit-transit1on: width 2s;
}
```

当设置 `extra-properties` 包含一个 `transit1on` 属性时，如下面所示
When `extra-properties` contains a property value of `transit1on` as show below:

```yaml
no-misspelled-properties:
  - 1
  -
    'extra-properties':
      - 'transit1on'
```

下面的写法是被允许的:

```scss

// 不正确的拼写现在在白名单中了
.baz {
  -webkit-transit1on: width 2s;
}

// 不正确的拼写现在在白名单中了
.quz {
  transit1on: width 2s;
}
```

下面的写法依然是不被允许的:

```scss

// 不正确的拼写
.foo {
  borders: 0;
}

// 未知的属性
.bar {
  border-right-left: 0;
}

```
