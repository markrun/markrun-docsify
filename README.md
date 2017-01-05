# markrun-docsify

[oneline](http://markrun.github.io/markrun-docsify/)

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <link rel="stylesheet" href="//unpkg.com/docsify/themes/vue.css">
</head>
<body>
  <div id="app"></div>
</body>

<script src="//unpkg.com/markrun/dist/markrun.min.js"></script>
<script src="//unpkg.com/prismjs" ></script>
<script>
window.$docsify = {
    markdown: function (marked) {
        markrun.setOptions({
            template: '',
            markdownParser: marked,
            highlight: function (source, lang, data) {
                return Prism.highlight(source,  Prism.languages[lang] || Prism.languages.markup)
            },
            compile: {
                js: function (source) {
                    // 如果需要编译则编译 source 后 eval
                    // eval 前必须增加 setTimeout
                    setTimeout(function () {
                        eval(source)
                    }, 100)
                    return {
                        lang: 'js',
                        source: source,
                        code: ''
                    }
                }
            }
        })
        return markrun
    }
}
</script>
<script src="//unpkg.com/docsify" data-router></script>
</html>

```
