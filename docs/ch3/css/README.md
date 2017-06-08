# nuxt中引入一个css文件的方式
***

### 方式1 css配置(nuxt.config.js)
这种方式引入的css文件放在每页的header style标签里,作为内联样式使用

```js
module.exports = {
    css: [
        'swiper/dist/css/swiper.css', // 引入第三方插件css
        '~assets/css/test.css', // 引入nuxt项目中的css
        { src: '~assets/scss/test.scss', lang: 'scss' } // 使用sass,同样可以使用less stylus
    ]
}
```
PS: 关于使用 sass(scss), less , stylus注意

1 必须先安装编译依赖
```js
npm install node-sass sass-loader --save-dev // 还要作为开发环境使用
```
2 css: [
    { src: '~assets/scss/test.scss', lang: 'scss' }
  ]
  
***  

### 方式2 header配置 (nuxt.config.js)
```js
module.exports = {
    link: [
          { rel: 'stylesheet', type: 'text/css', href: '/css/reset.css' }
    }
```
使用这种方式引入的css文件是作为外部css文件使用的,默认/是
指向static