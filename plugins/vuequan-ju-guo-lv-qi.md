<<<<<<< HEAD
=======

>>>>>>> 4558c9c7c8936b85f01e569a43d14da9ca93c9c9
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

<<<<<<< HEAD
{{ 123 \| rmb }}  结果为 ¥123

=======
{{ 123 \| rmb }}  结果为 ¥123`````
`````

6 疑问?
6.1 Q: import filters from '~components/filters'; 为什么我要将filters放在components这写目录才不报错误,放在根目录或者~plugins目录下报错
![](/assets/QQ截图20170605113218.png)

6.2 Q: 这样使用过滤Vue报警告,但是功能不影响
![](/assets/QQ截图20170605113409.png)
>>>>>>> 4558c9c7c8936b85f01e569a43d14da9ca93c9c9
