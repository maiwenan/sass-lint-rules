# 禁止使用某些属性

`no-disallowed-properties` 规则会对某些属性的使用进行警告。

## 可选的参数

* `properties`: `[禁止使用的属性组成的数组]` (默认为空数组 `[]`)。

## 例子

当 `properties` 包含一个 `z-index` 的属性值的时候，如下面所示:

```yaml
no-disallowed-properties:
  - 1
  -
    'properties':
      - 'z-index'
```

下面的写法是不被允许的:

```scss

// z-index 属性是不允许使用的
.foo {
  z-index: 10;
}

```
