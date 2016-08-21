# 禁止非法的十六进制值

`no-invalid-hex` 规则会强制只有合法的十六进制值才可以被使用（书写）。

## 例子

当启用时，任何非法的十六进制字符都会产生一个警告/错误:

```scss

// 一定要是 3 个或者 6 个字符
$invalid-long: #1234567;
$invalid-med: #1234;
$invalid-short: #12;
$invalid-letters-long: #abcdefg;
$invalid-letters-med: #abcd;
$invalid-letters-short: #ab;
$invalid-mixed-long: #1bcdefg;
$invalid-mixed-med: #1bcd;
$invalid-mixed-short: #1b;
$invalid-mixed-letters-long: #abcdef7;
$invalid-mixed-letters-med: #abc4;
$invalid-mixed-letters-short: #a1;

// 一定不能非法的字符
$invalid-character-map: (
  invalid-characters-upper-letters: #GHIJKL,
  invalid-characters-upper-letters-short: #GHI,
  even-more-invalid-map: (
    invalid-characters-lower-letters-short: #ghijkl,
    invalid-characters-lower-letters-short: #ghi
  )
);
```
