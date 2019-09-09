一: 检查运行环境对对ES6的支持

插件名称: [ES-Checker](https://github.com/ruanyf/es-checker)

Github地址:https://github.com/ruanyf/es-checker

二: 检查浏览器对Es6的支持

链接: http://ruanyf.github.io/es-checker/

三: 

js string转[number](https://blog.csdn.net/For_GG/article/details/78557966)

四: [restful 接口标准](https://blog.csdn.net/qq_41606973/article/details/86352787)

五: js十大[排序算法](https://www.cnblogs.com/beli/p/6297741.html)

六:  深拷贝[实现](https://blog.csdn.net/wang839305939/article/details/80819132)

深浅拷贝[实现](https://blog.csdn.net/weixin_37719279/article/details/81240658)

深拷贝的实现方式: 

1: 对象的属性赋值给另一个对象的属性(不适用复杂的数据)

2: Object.assign(同1)

3: 转成字符串再转回来

用`JSON.stringify`把对象转成字符串，再用`JSON.parse`把字符串转成新的对象。

```

var obj1 = { body: { a: 10 } };
var obj2 = JSON.parse(JSON.stringify(obj1));
obj2.body.a = 20;
console.log(obj1);
// { body: { a: 10 } } <-- 沒被改到
console.log(obj2);
// { body: { a: 20 } }
console.log(obj1 === obj2);
// false
console.log(obj1.body === obj2.body);
// false
```

4: 



七: js[数据类型](https://www.cnblogs.com/wanguofeng/p/10504090.html)

八: js Blob对象[类型](https://www.cnblogs.com/fps2tao/p/9267034.html)

九:iview tree[全选](https://www.jianshu.com/p/d2c1986b03ad)

十: vue单元测试[工具](https://www.qqxio.cn/article/84.html)

[单元测试](https://segmentfault.com/a/1190000014112447?utm_source=channel-newest)

十一: vue实现文件预览不同[后缀名](https://www.cnblogs.com/lhy-555/p/10839750.html)

十二: vue实现批量下载文件[打包](https://www.jb51.net/article/128583.htm)

```
import axios from 'axios'
import JSZip from 'jszip'
import FileSaver from 'file-saver'

const getFile = url => {
 return new Promise((resolve, reject) => {
 axios({
  method:'get',
  url,
  responseType: 'arraybuffer'
 }).then(data => {
  resolve(data.data)
 }).catch(error => {
  reject(error.toString())
 })
 })
}

export default {
 render(h) {
 return (<a on-click={ () => this.handleBatchDownload() } href="javascript:;" rel="external nofollow" >批量下载</a>)
 },
 methods: {
 handleBatchDownload() {
  const data = ['各类地址1', '各类地址2'] // 需要下载打包的路径, 可以是本地相对路径, 也可以是跨域的全路径
  const zip = new JSZip()
  const cache = {}
  const promises = []
  data.forEach(item => {
  const promise = getFile(item).then(data => { // 下载文件, 并存成ArrayBuffer对象
   const arr_name = item.split("/")
   const file_name = arr_name[arr_name.length - 1] // 获取文件名
   zip.file(file_name, data, { binary: true }) // 逐个添加文件
   cache[file_name] = data
  })
  promises.push(promise)
  })

  Promise.all(promises).then(() => {
  zip.generateAsync({type:"blob"}).then(content => { // 生成二进制流
   FileSaver.saveAs(content, "打包下载.zip") // 利用file-saver保存文件
  })
  })
 },
 },
}
```

十三: JS数据结构和[算法](https://www.cnblogs.com/roam/p/7423805.html)

[链表](https://www.jianshu.com/p/f254ec665e57)

十四: console[用法](https://www.cnblogs.com/liangzhixiaolaohu/p/8600905.html)

十五: 数组方法及[字典](https://www.cnblogs.com/bigberg/p/9237856.html)

十五: [CORDOVA](http://cordova.axuer.com/docs/zh-cn/latest/cordova/storage/storage.html)

```
function big () {
  var a = 222
  () => {
     console.log(a)
  }
}
```

十六: mysql安装[下载](https://blog.csdn.net/bobo553443/article/details/81383194)

十七: **ndoe+ mysql**

1: 新建文件夹

2: 进入文件夹cmd: node init

3: npm i 依赖 --save

依赖: body-parse, cookie-parse, cors, express,multer, mysql(操作数据库的js 插件)

4: 新建入口文件app.js,内容如下

```js
const express = require('express')
const app = express()
app.listen(8081, () => {
  console.log('服务器启动')
})
app.get('/', (req, res) => {
  res.send('helloworld')
})
```

res,req[参数](https://blog.csdn.net/yuhui01/article/details/81151045)

