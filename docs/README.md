# markrun

[https://github.com/markrun/markrun](https://github.com/markrun/markrun)

https://github.com/markrun/markrun-docsify

````html
time: <div class="demo" id="demo" ></div>
````

````js
document.getElementById('demo').innerHTML = new Date().getTime()
````

````css
.demo {
    color:blue;
}
````
<!--MARKRUN-HTML
<em>markrun/markrun</em>
-->


## react

<!--
{
    html: '<div id="_node"></div>'
}
-->
````js
var App = React.createClass({
    getInitialState: function () {
            return {
                count: 0
            }
    },
    render: function () {
        var self = this
        return (
            <div>
                <h3>{this.props.title}</h3>
                react time: {new Date().getTime()}
                <button type="button" onClick={function () {
                    self.setState({
                        count: self.state.count + 1
                    })
                }} >click: {self.state.count}</button>
            </div>
        )
    }
})
ReactDOM.render(<App title="some" />, document.getElementById('_node'))
````
