# ID 选择器命名风格

`id-name-format` 规则会强制 ID 选择器命名遵循一种规范。

## 可选的配置参数

* `allow-leading-underscore`: `true`/`false` (默认为 `true`)
* `convention`: `'hyphenatedlowercase'` (默认), `camelcase`, `snakecase`,或者一个类名匹配的正则表达式 (例如：`^[_A-Z]+&`)
* `convention-explanation`: 如果一个 ID 命名和规范不匹配，则把这个自定义的说明展示给用户。
* `ignore`: 一组被忽略的 ID 命名

## 例子 1

设置:
- `allow-leading-underscore: true`
- `convention: hyphenatedlowercase`
- `ignore: ['IGNORED_SELECTOR']`

使用上面设置时，下面的写法是被允许的:

```scss
#hyphenated-lowercase {
  content: '';

  &#_with-leading-underscore {
    content: '';
  }
}

#foo {
  @extend #hyphenated-lowercase;
}

#IGNORED_SELECTOR {
  content: '';
}

```

使用上面设置时，下面的写法是不被允许的:

```scss
#HYPHENATED-UPPERCASE {
  content: '';
}

#camelCase {
  content: '';

  @extend #snake_case;
}
```

## 例子 2

设置:
- `allow-leading-underscore: false`
- `convention: hyphenatedlowercase`

使用上面设置时，下面的写法是被允许的:

```scss
#hyphenated-lowercase {
  content: '';

  &#another-hyphenated-lowercase {
    content: '';
  }
}

#foo {
  @extend #hyphenated-lowercase;
}

```

使用上面设置时，下面的写法是不被允许的:

```scss
#_with-leading-underscore {
  content: '';
}

#HYPHENATED-UPPERCASE {
  content: '';
}

#camelCase {
  content: '';

  @extend #snake_case;
}
```

## 例子 3

设置:
- `convention: camelcase`

使用上面设置时，下面的写法是被允许的:

```scss
#camelCase {
  content: '';
}

#foo {
  @extend #anotherCamelCase;
}
```

## 例子 4

设置:
- `convention: pascalcase`

使用上面设置时，下面的写法是被允许的:

```scss
#PascalCase {
  content: '';
}

#Foo {
  @extend #AnotherPascalCase;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
#HYPHENATED-UPPERCASE {
  content: '';
}

#foo {
  @extend #snake_case;
}
```

## 例子 5

设置:
- `convention: snakecase`

使用上面设置时，下面的写法是被允许的:

```scss
#snake_case {
  content: '';
}

#foo {
  @extend #another_snake_case;
}
```

使用上面设置时，下面的写法是不被允许的:

```scss
#HYPHENATED-UPPERCASE {
  content: '';
}

#foo {
  @extend #camelCase;
}
```

## 例子 6

设置:
- `convention: ^[_A-Z]+$`
- `convention-explanation: 'IDs只能包括大写字母和下滑线'`

使用上面设置时，下面的写法是被允许的:

```scss
#SCREAMING_SNAKE_CASE {
  content: '';
}

#FOO {
  @extend #SCREAMING_SNAKE_CASE;
}
```

使用上面设置时，下面的写法是不被允许的:

(当进行检查时，带有 ID 的每一行都会报告 `IDs只能包括大写字母和下滑线`)

```scss
#HYPHENATED-UPPERCASE {
  content: '';
}

#snake_case {
  content: '';
}

#foo {
  @extend #camelCase;
}
```
