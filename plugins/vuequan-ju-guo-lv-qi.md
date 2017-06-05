
1 目录展示

![](/assets/filter.png)

2 创建filters/index.js 及 对应的过滤文件，这里我的是currency-filter.js

    // filters/currency-filter.js

    /**
     * 页面价格转换为货币格式过滤器
     */

    // 价格前面加上人民币符号
    export const rmb = (val) => {
      return `¥${val}`;
    };


```
// filters/index.js PS: 引入import模式, 导出必须export xxx {} 方式,webpack虽然(Commonjs与es6)语法都支持,但是两者不能混用

import { rmb } from './currency-filter';

export default{
  rmb
}
```

3 plugins/filters.js 

```
import Vue from 'vue';
import filters from '~components/filters';

// Vue注册全局过滤器
Object.keys(filters).forEach((key) => {
    return Vue.filter(key, filters[key])
});
// 箭头函数进一步简写与上面等价
// Object.keys(filters).forEach(key => Vue.filter(key, filters[key]))
```

4 nuxt配置\(nuxt.config.js\) 

```
 plugins: [
    { src: '~plugins/jquery.min.js', ssr: false }
 ]
```

5 页面使用过滤器 

{{ 123 \| rmb }}  结果为 ¥123

