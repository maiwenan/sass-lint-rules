# 简洁的值

`shorthand-values` 规则会强制简洁模式的值尽可能跟指定的一致。

## 可选的配置参数

* `allowed-shorthands`: `[允许的简洁的值的长度]` (defaults to `[1, 2, 3]`)

## 例子

当 `allowed-shorthands` 保持为默认的时候，下面的写法会被允许:

```yml
# .sass-lint.yml
shorthand-values: 1
```

```scss
margin: 1px 1px 1px 1px;

// 会被强制实施为1个值
margin: 1px;
```
```scss
margin: 1px 2px 1px 2px;

// 会被强制实施为2个值
margin: 1px 2px;
```
```scss
margin: 1px 2px 3px 2px;

// 会被强制实施为3个值
margin: 1px 2px 3px;
```

当 `allowed-shorthands` 设置为 `[1]` 的时候，下面的写法会被允许:

```yml
# .sass-lint.yml
shorthand-values:
  - 1
  -
    allowed-shorthands:
      - 1
```

```scss
margin: 1px 1px 1px 1px;

// 会被强制实施为1个值
margin: 1px;
```

任何不能被简洁成 1 个值的值都是不被允许的
```scss
// 可以被简洁成 2 个值，但是会产生一个警告
margin: 1px 2px 1px 2px;
```

当 `allowed-shorthands` 设置为 `[1, 2]` 的时候，下面的写法会被允许:

```yml
# .sass-lint.yml
shorthand-values:
  - 1
  -
    allowed-shorthands:
      - 1
      - 2
```

```scss
margin: 1px 1px 1px 1px;

// 会被强制实施为1个值
margin: 1px;
```

```scss
margin: 1px 2px 1px 2px;

// 会被强制实施为2个值
margin: 1px 2px;
```

任何不能被简洁成 2 个值的值都是不被允许的
```scss
// 可以被简洁成 2 个值，但是会产生一个警告
margin: 1px 2px 3px 2px;
```
