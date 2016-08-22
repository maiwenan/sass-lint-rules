# 变量命名风格

`variable-name-format` 规则会强制变量命名遵循一种规范。

## 可选的配置参数

* `allow-leading-underscore`: `true`/`false` (默认为 `true`)
* `convention`: `'hyphenatedlowercase'` (默认), `camelcase`, `snakecase`, [`strictbem`](https://en.bem.info/method/definitions/),
[`hyphenatedbem`](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/), 或者一个类名匹配的正则表达式 (例如：`^[_A-Z]+&`)
* `convention-explanation`: 如果一个变量命名和规范不匹配，则把这个自定义的说明展示给用户

## 例子 1

设置:
- `allow-leading-underscore: true`
- `convention: hyphenatedlowercase`

使用上面设置时，下面的写法是被允许的:

```scss
$hyphenated-lowercase: 1px;
$_leading-underscore: 1px;

.foo {
  width: $hyphenated-lowercase;
}

```

使用上面设置时，下面的写法是不被允许的:

```scss
$HYPHENATED-UPPERCASE: 1px;
$_camelCaseWithLeadingUnderscore: 1px;

.foo {
  width: $snake_case;
}
```

## 例子 2

设置:
- `allow-leading-underscore: false`
- `convention: camelcase`

使用上面设置时，下面的写法是被允许的:

```scss
$camelCase: 1px;

.foo {
  width: $anotherCamelCase;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
$HYPHENATED-UPPERCASE: 1px;
$_camelCaseWithLeadingUnderscore: 1px;

.foo {
  width: $snake_case;
}
```

## 例子 3

设置:
- `allow-leading-underscore: false`
- `convention: pascalcase`

使用上面设置时，下面的写法是被允许的:

```scss
$PascalCase: 1px;

.foo {
  width: $AnotherPascalCase;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
$HYPHENATED-UPPERCASE: 1px;
$_camelCaseWithLeadingUnderscore: 1px;

.foo {
  width: $snake_case;
}
```

## 例子 4

设置:
- `allow-leading-underscore: false`
- `convention: snakecase`

使用上面设置时，下面的写法是被允许的:

```scss
$snake_case: 1px;

.foo {
  width: $another_snake_case;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
$HYPHENATED-UPPERCASE: 1px;
$_snake_case_with_leading_underscore: 1px;

.foo {
  width: $camelCase;
}
```

## 例子 5

设置:
- `convention: strictbem`

使用上面设置时，下面的写法是被允许的:

```scss
$block-name__variable: 1px;
$block-name__variable_mod-name: 1px;
$block-name_mod-name__variable: 1px;

.foo {
  width: $block-name__variable;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
$HYPHENATED-UPPERCASE: 1px;

.foo {
  width: $camelCase;
}
```

## 例子 6

设置:
- `convention: hyphenatedbem`

使用上面设置时，下面的写法是被允许的:

```scss
$block-name__variable: 1px;
$block-name__variable--mod-name: 1px;
$block-name--mod-name__variable: 1px;

.foo {
  width: $block-name__variable;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
$HYPHENATED-UPPERCASE: 1px;

.foo {
  width: $camelCase;
}
```

## 例子 7

设置:
- `allow-leading-underscore: true`
- `convention: ^[_A-Z]+$`
- `convention-explanation: '变量只能包括大写字母和下滑线'`

使用上面设置时，下面的写法是被允许的:

```scss
$SCREAMING_SNAKE_CASE: 1px;

.foo {
  width: $_LEADING_UNDERSCORE;
}
```

使用上面设置时，下面的写法是不被允许的:

(当进行检查时，带有变量的每一行都会报告 `Mixins 只能包括大写字母和下滑线`)

```scss
$HYPHENATED-UPPERCASE: 1px;
$_snake_case_with_leading_underscore: 1px;

.foo {
  width: $camelCase;
}
```
