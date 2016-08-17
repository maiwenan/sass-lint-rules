# 强制伪元素/伪类选择器嵌套

`force-pseudo-nesting` 规则会强制伪元素/伪类选择器进行嵌套书写。


## 例子

当启用时，下面的写法是不被允许的:

```scss
p:nth-of-type(2) {
  margin: 0;
}

.parent {
  .child {
    p::first-line {
      color: #ff0000;
    }
  }
}

.parent {
  .child {
    .sub p::first-line {
      color: #ff0000;
    }
  }
}
```

当启用时，下面的写法是被允许的:

```scss
p {
  &:nth-of-type(2) {
    margin: 0;
  }
}

.parent {
  .child {
    p {
      &::first-line {
        color: #ff0000;
      }
    }
  }
}

.parent {
  .child {
    .sub p {
      &::first-line {
        color: #ff0000;
      }
    }
  }
}
```
