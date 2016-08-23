# Sass Lint Rules [![Build Status](https://travis-ci.org/maiwenan/sass-lint-rules.svg?branch=master)](https://travis-ci.org/maiwenan/sass-lint-rules)

[sass-lint](https://github.com/sasstools/sass-lint) 所定义的规则的翻译，并提供了一份 `sass` 的编码规范。

---

## 下载

你可以从 [NPM](https://www.npmjs.com/package/sass-lint) 上下载 `sass-lint-rules` :

```
npm install --save-dev sass-lint-rules
```

## 使用

* 如果你想要完全使用 `sass-lint-rules` 提供的 `sass` 编码规范，你可以直接指定 `.sass-lint.yml` 为配置文件，比如:

```
sass-lint -c node_modules/sass-lint-rules/.sass-lint.yml -v -q
```

* 如果你需要自定义部分规则，那么你可以在你的 `sass-lint` 配置文件的 `config-file` 属性中指定加载 `sass-lint-rules` 提供的配置文件，比如:

```
options:
	config-file: node_modules/sass-lint-rules/.sass-lint.yml
```
