# Mixin 命名风格

`mixin-name-format` 规则会强制 mixin 命名遵循一种规范。
Rule `mixin-name-format` will enforce a convention for mixin names.

## 可选的配置参数

* `allow-leading-underscore`: `true`/`false` (默认为 `true`)
* `convention`: `'hyphenatedlowercase'` (默认), `camelcase`, `snakecase`, [`strictbem`](https://en.bem.info/method/definitions/),
[`hyphenatedbem`](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/), 或者一个变量名匹配的正则表达式 (例如：`^[_A-Z]+&`)
* `convention-explanation`: 如果一个 mixin 的命名和规范不匹配，则把这个自定义的说明展示给用户。

## 例子 1

设置:
- `allow-leading-underscore: true`
- `convention: hyphenatedlowercase`

使用上面设置时，下面的写法是被允许的:

```scss
@mixin hyphenated-lowercase() {
  content: '';
}

@mixin _leading-underscore() {
  content: '';
}

.foo {
  @include hyphenated-lowercase();
}

```

使用上面设置时，下面的写法是不被允许的:

```scss
@mixin HYPHENATED-UPPERCASE() {
  content: '';
}

@mixin _camelCaseWithLeadingUnderscore() {
  content: '';
}

.foo {
  @include snake_case();
}
```

## 例子 2

设置:
- `allow-leading-underscore: false`
- `convention: camelcase`

使用上面设置时，下面的写法是被允许的:

```scss
@mixin camelCase() {
  content: '';
}

.foo {
  @include anotherCamelCase();
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
@mixin HYPHENATED-UPPERCASE() {
  content: '';
}

@mixin _camelCaseWithLeadingUnderscore() {
  content: '';
}

.foo {
  @include snake_case();
}
```

## 例子 3

设置:
- `allow-leading-underscore: false`
- `convention: pascalcase`

使用上面设置时，下面的写法是被允许的:

```scss
@mixin PascalCase() {
  content: '';
}

.foo {
  @include AnotherPascalCase();
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
@mixin HYPHENATED-UPPERCASE() {
  content: '';
}

@mixin _camelCaseWithLeadingUnderscore() {
  content: '';
}

.foo {
  @include snake_case();
}
```

## 例子 4

设置:
- `allow-leading-underscore: false`
- `convention: snakecase`

使用上面设置时，下面的写法是被允许的:

```scss
@mixin snake_case() {
  content: '';
}

.foo {
  @include another_snake_case();
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
@mixin HYPHENATED-UPPERCASE() {
  content: '';
}

@mixin _snake_case_with_leading_underscore() {
  content: '';
}

.foo {
  @include camelCase();
}
```

## 例子 5

设置:
- `convention: strictbem`

使用上面设置时，下面的写法是被允许的:

```scss
@mixin block-name {
  content: '';
}

@mixin block-name__mixin {
  content: '';
}

@mixin block-name_mod-name {
  content: '';
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
@mixin HYPHENATED-UPPERCASE {
  content: '';
}

.foo {
  @include camelCase();
}
```

## 例子 6

设置:
- `convention: hyphenatedbem`

使用上面设置时，下面的写法是被允许的:

```scss
@mixin block-name {
  content: '';
}

@mixin block-name__mixin {
  content: '';
}

@mixin block-name--mod-name {
  content: '';
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
@mixin HYPHENATED-UPPERCASE {
  content: '';
}

.foo {
  @include camelCase();
}
```


## 例子 7

设置:
- `allow-leading-underscore: true`
- `convention: ^[_A-Z]+$`
- `convention-explanation: 'mixin 只能包括大写字母和下滑线'`

使用上面设置时，下面的写法是被允许的:

```scss
@mixin SCREAMING_SNAKE_CASE() {
  content: '';
}

.foo {
  @include _LEADING_UNDERSCORE();
}
```

使用上面设置时，下面的写法是不被允许的:

(当进行检查时，带有 mixin 变量的每一行都会报告 `mixin 只能包括大写字母和下滑线`)

```scss
@mixin HYPHENATED-UPPERCASE() {
  content: '';
}

@mixin _snake_case_with_leading_underscore() {
  content: '';
}

.foo {
  @include camelCase();
}
```
