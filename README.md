<!--
 * @Date: 2021-05-24 15:08:24
 * @LastEditors: Timothy
 * @LastEditTime: 2021-05-25 12:05:28
 * @Description: 
-->
# todolist-vue3.x

## git分支发布流程

`git subtree split --prefix dist -b gh-pages`
`git push -f origin gh-pages:gh-pages`
`git branch -D gh-pages`
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
