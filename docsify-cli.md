# docsify-cli

## 简介

文档生成工具。

> docsify cli - A magical documentation generator.

## 网址

* [docsify官网/文档](https://docsify.js.org/#/)
* [github](https://github.com/docsifyjs/docsify)
* [案例](https://github.com/docsifyjs/awesome-docsify#showcase)

## Screencast

![Screencast](https://raw.githubusercontent.com/QingWei-Li/docsify-cli/master/media/screencast.gif)

> Running a server on `localhost` with live-reload.

## 安装

通过 `npm` 或 `yarn` 全局安装 `docsify-cli`。

```shell
npm i docsify-cli -g
# yarn global add docsify-cli
```

## 使用

### `init` 命令

使用 `init` 初始化文档项目。

```shell
docsify init <path> [--local false] [--theme vue]

# docsify i <path> [--local false] [--theme vue]
```

示例：

```shell
# 建议使用 --local，避免服务启动报错
docsify init docs --local
```

`<path>` defaults to the current directory. Use relative paths like `./docs` (or `docs`).

* `--local` option:
  * Shorthand: `-l`
  * Type: boolean
  * Default: `false`
  * Description: Copy `docsify` files to the docs path, defaults to `false` using `unpkg.com` as the content delivery network (CDN). To explicitly set this option to `false` use `--no-local`.
* `--theme` option:
  * Shorthand: `-t`
  * Type: string
  * Default: `vue`
  * Description: Choose a theme, defaults to `vue`, other choices are `buble`, `dark` and `pure`.

### `serve` 命令

Run a server on `localhost` with livereload.

```shell
docsify serve <path> [--open false] [--port 3000]

# docsify s <path> [--open false] [--port 3000]
```

示例：

```
docsify serve docs --open --port 3000
```

* `--open` option:
  * Shorthand: `-o`
  * Type: boolean
  * Default: `false`
  * Description: Open the docs in the default browser, defaults to `false`. To explicitly set this option to `false` use `--no-open`.
* `--port` option:
  * Shorthand: `-p`
  * Type: number
  * Default: `3000`
  * Description: Choose a listen port, defaults to `3000`.

## License

MIT
