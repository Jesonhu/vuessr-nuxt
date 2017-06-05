# **vue-awesome-swiper组件使用**

1 package.json 安装依赖

```
npm install vue-awesome-swiper --save
```

2 vue框架使用改插件: 创建plugins/swiper.js

```
import Vue from 'vue'
import VueAwesomeSwiper from 'vue-awesome-swiper/ssr'

Vue.use(VueAwesomeSwiper);
```

3 nuxt服务端配置\(nuxt.config.js\)

    module.exports = {
        css: [
            `swiper/dist/css/swiper.css` // 引入swiper的css文件
        ],
        build: {
            vendor: [
                'swiper' // 避免多次引入多次加载swiper资源文件
            ]
        }
        plugins: [
            { src: '~plugins/swiper.js', ssr: false } // 引入swiper的js文件
        ]
    }

4 页面使用swiper插件

```
<template>
  <div class="swiper" v-swiper:swiper="swiperOption">
      <!-- 内容区域 -->
      <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="item in bannerList">
          <a :href="item.link" class="link">
            <img :src="item.picUrl" alt="">
          </a>
        </div>
      </div>
      <!-- 前进后退按钮 -->
      <div class="swiper-button-prev"></div>
      <div class="swiper-button-next"></div>
      <!-- 内容显示导航 -->
      <div class="bottom-nav swiper-pagination"></div>
  </div>
</template>     

<script>
  export default {
    data() {
      return {
        swiperOption: {
          autoplay: 3500,
          setWrapperSize: false, // 开启flex宽度为item宽度总和
          autoHeight: true,
          pagination: '.swiper-pagination',
          paginationClickable: true,
          prevButton:'.swiper-button-prev',
          nextButton:'.swiper-button-next',
          mousewheelControl: false,
          autoplayDisableOnInteraction: false,
          observeParents: true,
          grabCursor: true,
          preloadImages: false,
          lazyLoading: true
        }
      }
    }
  }
</script>
```

5 注意事项

5.1 swiper-wrapper\(父\)  swiper-slide\(子\) 两者关系固定

