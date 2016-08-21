# 禁止重复的属性

`no-duplicate-properties` 规则会强制在同一个样式块中不能出现重复的属性。

## 可选的配置参数

* `exclude`: `[一组被排除掉的属性名]` (默认为空数组 `[]`)


## 例子

当启用时，下面的写法是不被允许的:

```scss
.foo {
  margin: 0 0 15px;
  margin: 0;
}
```

### 不包含

当一个属性被添加到不包含数组时，如下面所示的，你才可以紧接着另外一个属性去放置重复的属性，这是为了避免意料之外的重复属性。

```yml
no-duplicate-properties:
  - 1
  -
    exclude:
      - display
```

当 `display` 属性被添加到不包含数组中时，下面的写法是被允许的:

```scss
.display-block {
  display: flex;
  display: inline-block;
  float: right;
}
```

当 `display` 属性被添加到不包含数组中时，下面的写法依然是不被允许的，因为重复的属性被其他的属性分隔开了:

```scss
.display-block {
  display: flex;
  float: right;
  display: inline-block;
}
```
