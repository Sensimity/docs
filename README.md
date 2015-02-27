# Sensimity API documentation project
The documentation is written in Markdown (yes, [GitHub flavoured](http://www.mkdocs.org/)) and we use [mkdocs](http://www.mkdocs.org/) to build it.

## Building the docs
Make sure you have [mkdocs](http://www.mkdocs.org/) installed on your system.

You can then build the docs via the following command:

```sh
$ mkdocs build --clean
```

The docs are best viewed via your browser, so start a webserver:

```sh
$ php -S 127.0.0.1:8080 -t site/
```

And view them in your browser:
```sh
open http://127.0.0.1:8080/
```

## Editors
Some suggestions for editors:

* [Mou](http://25.io/mou/) (for Mac)
* [Online editor](http://jbt.github.io/markdown-editor/)
* PhpStorm with [MD plugin](https://plugins.jetbrains.com/plugin/5970?pr=phpStorm)