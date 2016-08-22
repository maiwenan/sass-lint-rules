# 占位符命名风格

`placeholder-name-format` 规则会强制占位符命名遵循一种规范。

## 可选的配置参数

* `allow-leading-underscore`: `true`/`false` (默认为 `true`)
* `convention`: `'hyphenatedlowercase'` (默认), `camelcase`, `snakecase`, [`strictbem`](https://en.bem.info/method/definitions/),
[`hyphenatedbem`](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/), 或者一个类名匹配的正则表达式 (例如：`^[_A-Z]+&`)
* `convention-explanation`: 如果一个占位符命名和规范不匹配，则把这个自定义的说明展示给用户

## 例子 1

设置:
- `allow-leading-underscore: true`
- `convention: hyphenatedlowercase`

使用上面设置时，下面的写法是被允许的:

```scss
%hyphenated-lowercase {
  content: '';
}

%_leading-underscore {
  content: '';
}

.foo {
  @extend %hyphenated-lowercase;
}

```

使用上面设置时，下面的写法是不被允许的:

```scss
%HYPHENATED-UPPERCASE {
  content: '';
}

%_camelCaseWithLeadingUnderscore {
  content: '';
}

.foo {
  @extend %snake_case;
}
```

## 例子 2

设置:
- `allow-leading-underscore: false`
- `convention: camelcase`

使用上面设置时，下面的写法是被允许的:

```scss
%camelCase {
  content: '';
}

.foo {
  @extend %anotherCamelCase;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
%HYPHENATED-UPPERCASE {
  content: '';
}

%_camelCaseWithLeadingUnderscore {
  content: '';
}

.foo {
  @extend %snake_case;
}
```

## 例子 3

设置:
- `allow-leading-underscore: false`
- `convention: pascalcase`

使用上面设置时，下面的写法是被允许的:

```scss
%PascalCase {
  content: '';
}

.foo {
  @extend %AnotherPascalCase;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
%HYPHENATED-UPPERCASE {
  content: '';
}

%_camelCaseWithLeadingUnderscore {
  content: '';
}

.foo {
  @extend %snake_case;
}
```

## 例子 4

设置:
- `allow-leading-underscore: false`
- `convention: snakecase`

使用上面设置时，下面的写法是被允许的:

```scss
%snake_case {
  content: '';
}

.foo {
  @extend %another_snake_case;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
%HYPHENATED-UPPERCASE {
  content: '';
}

%_snake_case_with_leading_underscore {
  content: '';
}

.foo {
  @extend %camelCase;
}
```

## 例子 5

设置:
- `convention: strictbem`

使用上面设置时，下面的写法是被允许的:

```scss
%block-name {
  content: '';
}

%block-name__mixin {
  content: '';
}

%block-name_mod-name {
  content: '';
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
%HYPHENATED-UPPERCASE {
  content: '';
}

.foo {
  @extend %camelCase;
}
```

## 例子 6

设置:
- `convention: hyphenatedbem`

使用上面设置时，下面的写法是被允许的:

```scss
%block-name {
  content: '';
}

%block-name__mixin {
  content: '';
}

%block-name--mod-name {
  content: '';
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
%HYPHENATED-UPPERCASE {
  content: '';
}

.foo {
  @extend %camelCase;
}
```

## 例子 7

设置:
- `allow-leading-underscore: true`
- `convention: ^[_A-Z]+$`
- `convention-explanation: 'Mixins 只能包括大写字母和下滑线'`

使用上面设置时，下面的写法是被允许的:

```scss
%SCREAMING_SNAKE_CASE {
  content: '';
}

.foo {
  @extend %_LEADING_UNDERSCORE;
}
```

使用上面设置时，下面的写法是不被允许的:

(当进行检查时，带有占位符的每一行都会报告 `Mixins 只能包括大写字母和下滑线`)

```scss
%HYPHENATED-UPPERCASE {
  content: '';
}

%_snake_case_with_leading_underscore {
  content: '';
}

.foo {
  @extend %camelCase;
}
```
