[toc]


### babel插件
babel编译流程
parse -> transfrom -> generate

```javascript
const targetCalleeName = ['log', 'info', 'error', 'debug'].map(item => `console.${item}`);

const parametersInsertPlugin = ({ types }, options) => {
    return {
        visitor: {
            CallExpression(path, state) {
                const calleeName = path.get('callee').toString()
                if (targetCalleeName.includes(calleeName)) {
                   const { line, column } = path.node.loc.start;
                   path.node.arguments.unshift(types.stringLiteral(`${options.file.filename}: (${line}, ${column})`))
               }
            }
        }
    }
}
module.exports = parametersInsertPlugin;
```





































