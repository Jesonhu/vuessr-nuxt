## 使用场景: 给axios请求地址配置域以及Nuxt全局域

###### nuxt dev配置(nuxt.config.js) 配置Nuxt全局域
```js
env: {
    baseUrl: process.env.BASE_URL || 'http://127.0.0.1:3000'
}
```

###### plugins/axios.js
```js
import axios from 'axios';

export default axios.create({
  baseURL: process.env.baseUrl
});
```

###### 页面使用axios插件 如果没有配置地址前面要加上域
例如: axios.get('http://127.0.0.1:3000/api/common.json')
```js
import axios from '~plugins/axios'

axios.get('/api/common.json');
```
###### 这样使用命令行有警告,但是不影响功能
![](../../../assets/filter_dependency.png)

##### 问题1
问题: filter文件夹现在只能放在
components下,放其他会报错
![](../../../assets/filter-error.png) 