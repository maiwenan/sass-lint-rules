# 类名书写规范

`class-name-format` 会为类名约定一个规范。

### 可选的配置参数

* `allow-leading-underscore`: `true`/`false` (默认为 `true`)
* `convention`: `'hyphenatedlowercase'` (默认)，`camelcase`，`snakecase`,
[`strictbem`](https://en.bem.info/method/definitions/),
[`hyphenatedbem`](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/),
或者一个类名匹配的正则表达式 (例如：`^[_A-Z]+&`)
* `convention-explanation`: 如果一个类名和规范不匹配，则把这个自定义的说明展示给用户。
* `ignore`: 一组被忽略的类名

## 例子 1

设置:
- `allow-leading-underscore: true`
- `convention: hyphenatedlowercase`

使用上面设置时，下面的写法是被允许的:

```scss
.hyphenated-lowercase {
  content: '';

  &._with-leading-underscore {
    content: '';
  }
}

.foo {
  @extend .hyphenated-lowercase;
}

```

使用上面设置时，下面的写法不是被允许的:

```scss
.HYPHENATED-UPPERCASE {
  content: '';
}

.camelCase {
  content: '';

  @extend .snake_case;
}
```

## 例子 2

设置:
- `allow-leading-underscore: false`
- `convention: hyphenatedlowercase`

使用上面设置时，下面的写法是被允许的:

```scss
.hyphenated-lowercase {
  content: '';

  &.another-hyphenated-lowercase {
    content: '';
  }
}

.foo {
  @extend .hyphenated-lowercase;
}

```

使用上面设置时，下面的写法不是被允许的:

```scss
._with-leading-underscore {
  content: '';
}

.HYPHENATED-UPPERCASE {
  content: '';
}

.camelCase {
  content: '';

  @extend .snake_case;
}
```

## 例子 3

设置:
- `convention: camelcase`

使用上面设置时，下面的写法是被允许的:

```scss
.camelCase {
  content: '';
}

.foo {
  @extend .anotherCamelCase;
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
.HYPHENATED-UPPERCASE {
  content: '';
}

.foo {
  @extend .snake_case;
}
```

## 例子 4

设置:
- `convention: pascalcase`

使用上面设置时，下面的写法是被允许的:

```scss
.PascalCase {
  content: '';
}

.Foo {
  @extend .AnotherPascalCase;
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
.HYPHENATED-UPPERCASE {
  content: '';
}

.foo {
  @extend .snake_case;
}
```

## 例子 5

设置:
- `convention: snakecase`

使用上面设置时，下面的写法是被允许的:

```scss
.snake_case {
  content: '';
}

.foo {
  @extend .another_snake_case;
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
.HYPHENATED-UPPERCASE {
  content: '';
}

.foo {
  @extend .camelCase;
}
```

## 例子 6

设置:
- `convertion: strictbem`

使用上面设置时，下面的写法是被允许的:

```scss
.block-name__elem-name {
  content: '';
}

.owner-name_mod-name_mod-val {
  content: '';
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
.HYPHENATED-UPPERCASE {
  content: '';
}

.foo {
  @extend .camelCase;
}
```

## 例子 7

设置:
- `convertion: hyphenatedbem`

使用上面设置时，下面的写法是被允许的:

```scss
.site-search {
  color: blue;
  width: 50px;
  height: 100%;
}

.site-search__field {
  text-decoration: underline;
}

.site-search--full {
  color: green;
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
.HYPHENATED-UPPERCASE {
  content: '';
}

.foo {
  @extend .camelCase;
}
```

## 例子 8

设置:
- `convertion: ^[_A-Z]+&`
- `convention:-explanation: '类名只能包括大写字母和下滑线'`

使用上面设置时，下面的写法是被允许的:

```scss
.SCREAMING_SNAKE_CASE {
  content: '';
}

.foo {
  @extend .SCREAMING_SNAKE_CASE;
}
```

使用上面设置时，下面的写法不是被允许的:

(当进行检查时，带有类名的每一行都会报告 `类名只能包括大写字母和下滑线`)

```scss
.HYPHENATED-UPPERCASE {
  content: '';
}

.snake_case {
  content: '';
}

.foo {
  @extend .camelCase;
}
```
