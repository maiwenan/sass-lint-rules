# 属性值的单位

`property-units` 规则不允许使用没有在 `global` 或者 `per-property` 中指定的单位。某个特定的属性在 `per-property` 中指定的单位会覆盖在 `global` 中指定的单位。

## 可选的配置参数

* `global`: `['em', 'px', 'rem', etc]` 默认为 [] 或者所有单位都可以使用
* `per-property`: `{ width: ['rem', 'px', etc], height: ['rem', 'px', etc], }` 默认为 {} 或者没有为某个属性指定单位。

## 例子

当启用时，`global` 设置为 `['px']` ，而且 `per-property` 设置为 `{ width: ['rem'] }` ，下面的写法是不被允许的:

```scss
.literal {
    height: 3rem;
}

.literal-property {
    width: 3px;
}

.box-shadow {
  box-shadow: 1em 1em black, 1em 1em black;
}

.background {
  background: 1em solid white;
}

```

当启用时，`global` 设置为 `['em']` ，而且 `per-property` 设置为 `{ width: ['rem'] }` ，下面的写法是被允许的:

```scss

.variable {
    width: $sizes.small;
}

.function {
  color: test(2px);
}

//  使用文字作为属性名字
$sizes: (
  small: 2px
);
```
