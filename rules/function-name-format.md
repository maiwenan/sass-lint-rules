# 方法命名的风格

`function-name-format` 规则会强制方法命名遵循一种规范。

## 可选的配置参数

* `allow-leading-underscore`: `true`/`false` (默认为 `true`)
* `convention`: `'hyphenatedlowercase'` (默认), `camelcase`, `snakecase`, [`strictbem`](https://en.bem.info/method/definitions/),
[`hyphenatedbem`](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/), 或者一个类名匹配的正则表达式 (例如：`^[_A-Z]+&`)
* `convention-explanation`: 如果一个类名和规范不匹配，则把这个自定义的说明展示给用户。

## 例子 1

设置:
- `allow-leading-underscore: true`
- `convention: hyphenatedlowercase`

使用上面设置时，下面的写法是被允许的:

```scss
@function hyphenated-lowercase() {
  @return "foo";
}

@function _leading-underscore($x) {
  @return $x;
}

.foo {
  content: hyphenated-lowercase("bar");
}
```
使用上面设置时，下面的写法不是被允许的:

```scss
@function HYPHENATED-UPPERCASE() {
  @return "foo";
}

@function _camelCaseWithLeadingUnderscore($x) {
  @return $x;
}

.foo {
  content: snake_case();
}
```

## 例子 2

设置:
- `allow-leading-underscore: false`
- `convention: camelcase`

使用上面设置时，下面的写法是被允许的:

```scss
@function camelCase() {
  @return "foo";
}

.foo {
  content: anotherCamelCase();
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
@function HYPHENATED-UPPERCASE() {
  @return "foo";
}

@function _camelCaseWithLeadingUnderscore() {
  @return "foo";
}

.foo {
  content: snake_case();
}
```

## 例子 3

设置:
- `allow-leading-underscore: false`
- `convention: pascalcase`

使用上面设置时，下面的写法是被允许的:

```scss
@function PascalCase() {
  @return "foo";
}

.foo {
  content: AnotherPascalCase();
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
@function HYPHENATED-UPPERCASE() {
  @return "foo";
}

@function _camelCaseWithLeadingUnderscore() {
  @return "foo";
}

.foo {
  content: snake_case();
}
```

## 例子 4

设置:
- `allow-leading-underscore: false`
- `convention: snakecase`

使用上面设置时，下面的写法是被允许的:

```scss
@function snake_case() {
  @return "foo";
}

.foo {
  content: another_snake_case();
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
@function HYPHENATED-UPPERCASE() {
  @return "foo";
}

@function _snake_case_with_leading_underscore() {
  @return "foo";
}

.foo {
  content: camelCase();
}
```

## 例子 5

设置:
- `convention: strictbem`

使用上面设置时，下面的写法是被允许的:

```scss
@function namespace__function {
  @return "foo";
}

@function namespace__function_mod-name {
  @return "foo";
}

@function namespace_mod-name__function {
  @return "foo";
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
@function HYPHENATED-UPPERCASE {
  @return "foo";
}

.foo {
  content: camelCase();
}
```

## 例子 6

设置:
- `convention: hyphenatedbem`

使用上面设置时，下面的写法是被允许的:

```scss
@function namespace__function {
  @return "foo";
}

@function namespace__function--mod-name {
  @return "foo";
}

@function namespace--mod-name__function {
  @return "foo";
}
```

使用上面设置时，下面的写法不是被允许的:

```scss
@function HYPHENATED-UPPERCASE {
  @return "foo";
}

.foo {
  content: camelCase();
}
```

## 例子 7

设置:
- `allow-leading-underscore: true`
- `convention: '^[_A-Z]+$'`
- `convention-explanation: '方法只能包括大写字母和下滑线'`

使用上面设置时，下面的写法是被允许的:

```scss
@function SCREAMING_SNAKE_CASE() {
  @return "foo";
}

.foo {
  content: _LEADING_UNDERSCORE();
}
```

使用上面设置时，下面的写法不是被允许的:

(当进行检查时，带有方法调用/声明的每一行都会报告 `方法只能包括大写字母和下滑线`)

```scss
@function HYPHENATED-UPPERCASE() {
  @return "foo";
}

@function _snake_case_with_leading_underscore() {
  @return "foo";
}

.foo {
  content: camelCase();
}
```
