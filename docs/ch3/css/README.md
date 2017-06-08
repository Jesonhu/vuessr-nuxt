# nuxt中引入一个css文件的方式
***

### 方式1 css: []

```js
module.exports = {
    css: [
        'swiper/dist/css/swiper.css', // 引入第三方插件css
        '~assets/css/test.css' // 引入nuxt项目中的css
    ]
}
```