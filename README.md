<!--
 * @Date: 2021-05-24 15:08:24
 * @LastEditors: Timothy
 * @LastEditTime: 2021-05-25 14:24:42
 * @Description: 
-->
# todolist-vue3.x

## git分支发布流
`git subtree split --prefix dist -b gh-pages`
`git push -f origin gh-pages:gh-pages`
`git branch -D gh-pages`
可能出现的问题：
如果内容没有变化，打包出来的东西可能不会发生变化，会导致`git push` 出现 `Everything up-to-date` 
## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
