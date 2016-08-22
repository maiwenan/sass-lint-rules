# 伪元素/类

`pseudo-element` 规则会强制:
* Pseudo-**element** 一定要以两个冒号开始。
* Pseudo-**classes** 一定要以一个冒号开始。

## 例子

当启用时，下面的写法是被允许的:

```scss
.foo::before {
  content: "bar";
}

.foo:hover {
  content: "bar";
}
```

当启用时，下面的写法是不被允许的:

```scss
.foo:before {
  content: "bar";
}

.foo::hover {
  content: "bar";
}
```
