# markrun-docsify

[online](http://markrun.github.io/markrun-docsify/)

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
<!--  不需要编译 react jsx 则删除这些 script Start -->
<script src="//unpkg.com/es5-shim/es5-shim.min.js"></script>
<script src="//unpkg.com/es5-shim/es5-sham.min.js"></script>
<script src="//unpkg.com/console-polyfill"></script>
<script src="//unpkg.com/react@0.14.8/dist/react.min.js"></script>
<script src="//unpkg.com/react-dom@0.14.8/dist/react-dom.min.js"></script>
<script src="//unpkg.com/react@0.13.1/dist/JSXTransformer.js"></script>
<!--  不需要编译 react jsx 则删除这些 script End -->

<script src="//unpkg.com/markrun/dist/markrun.min.js" ></script>
<script>
window.$docsify = {
    markdown: function (marked) {
        markrun.setOptions({
            template: '',
            markdownParser: marked,
            compile: {
                js: function (source) {
                    // 如果需要编译则编译 source 后 eval
                    // eval 前必须增加 setTimeout
                    setTimeout(function () {
                        if (JSXTransformer) {
                            source = JSXTransformer.transform(source).code
                        }
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
<script src="https://unpkg.com/docsify@3.7.3/lib/docsify.js"  data-router ></script>
</html>
```
