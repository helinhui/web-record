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

**十六:** mysql安装[下载](https://blog.csdn.net/bobo553443/article/details/81383194)

**十七**: **node+ mysql**

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

**十八**: JS进阶[类](https://jingyan.baidu.com/article/4b52d702c6cd87fc5d774b57.html)

```js
class Car {
      constructor (maker, price) {
        this.maker = maker
        this.price = price
      }
      getInfo () {
        console.log(this.maker)
      }
    }
    var car1 = new Car('hahha', '123')
    car1.getInfo()
    console.log(typeof (Car))
```

![](D:\Project\markdown\类.png)

**十九**:[Vue.js中使用iView日期选择器并设置开始时间结束时间校验](https://www.cnblogs.com/xiaguliuxiang/p/9459917.html)

```js
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <title>Vue.js中使用iView日期选择器并设置开始时间结束时间校验</title>
    <!-- import Vue.js -->
    <script src="https://vuejs.org/js/vue.min.js"></script>
    <!-- import stylesheet -->
    <link rel="stylesheet" href="https://unpkg.com/iview/dist/styles/iview.css">
    <!-- import iView -->
    <script src="https://unpkg.com/iview/dist/iview.min.js"></script>
</head>

<body>
    <div id="app">
        <template>
            <Row>
                <Col span="12"> 开始时间:
                <date-picker type="datetime" v-model="startTime" placeholder="请选择开始时间" :options="startTimeOption" @on-change="onStartTimeChange"></date-picker>
                </Col>
                <Col span="12"> 结束时间:
                <date-picker type="datetime" v-model="endTime" placeholder="请选择结束时间" :options="endTimeOption" @on-change="onEndTimeChange"></date-picker>
                </Col>
            </Row>
        </template>
    </div>

    <script>
        new Vue({
            el: '#app',
            data() {
                return {
                    startTime: '',
                    endTime: '',
                    startTimeOption: {},
                    endTimeOption: {}
                }
            },
            mounted() {
                this.startTime = '2018-08-08 00:00:00'
                this.endTime = '2018-08-11 23:59:59'
                this.onStartTimeChange(this.startTime)
                this.onEndTimeChange(this.endTime)
            },
            methods: {
                /**
                 * 开始时间发生变化时触发,设置结束时间不可选择的日期
                 * 结束时间应大于等于开始时间,且小于等于当前时间
                 * @param {string} startTime 格式化后的日期
                 * @param {string} type 当前的日期类型
                 */
                onStartTimeChange(startTime, type) {
                    this.endTimeOption = {
                        disabledDate(endTime) {
                            return endTime < new Date(startTime) || endTime > Date.now()
                        }
                    }
                },
                /**
                 * 结束时间发生变化时触发,设置开始时间不可选择的日期
                 * 开始时间小于等于结束时间,且小于等于当前时间
                 * @param {string} date 格式化后的日期
                 * @param {string} type 当前的日期类型
                 */
                onEndTimeChange(endTime, type) {
                    this.startTimeOption = {
                        disabledDate(startTime) {
                            return startTime > new Date(endTime) || startTime > Date.now()
                        }
                    }
                }
            }
        })
    </script>
</body>

</html>
```

二十: 换算时间

d.getTime() -- 获取当前时间，单位 将是 毫秒。（时间坐标原点由 Date class 约定好的）
exdays * 24 * 60 * 60 * 1000 -- 附加多少天，换算成 毫秒
d.setTime（当前时间 + 附加时间） -- 设Date class 的对象 d 的 时间值 等于 （当前时间 + 附加时间），即目标时间。
然后可以用想要的格式输出目标时间的 年月日时分秒。

```js
value () {
 const date = new Date()
 date.setTime(date.getTime() - 3600 * 1000 * 24)
 return date
}


// 前一天和后一天
Date curDate = new Date()
// 前一天
var preDate = new Date(curDate.getTime() - 24*60*60*1000)
// 后一天
var nextDate = new Date(curDate.getTime() + 24*60*60*1000)


```

**二十一:**[递归](https://blog.csdn.net/chad97/article/details/82729021)

```js
var i=0;
function f1() {
 i++;
 (i<5) {
   f1();
 }
  console.log("从前有座山，山里有个庙，庙里有个老和尚给小和尚讲故     事：");
};
f1();



 // 求n个数字的和 n=5 ——->5+4+3+2+1
//for 循环写法：
var sum=0;
for (var i=0;i<=5;i++){
  sum+=i;
}
 console.log(sum);
----------------------分割线---------------------------

   function getSum(x) {
        if (x==1){
          return 1
        }
        return x+getSum(x-1);
    };

    var sum1=getSum(5);
    console.log(sum1);
    console.log(getSum(10));



```

**二十二:** **[h5 video](https://blog.csdn.net/weixin_41578603/article/details/81168466)**

**二十三:** render添加[img](http://www.mamicode.com/info-detail-2328296.html)

标签：[http](http://www.mamicode.com/so/1/http)   [AC](http://www.mamicode.com/so/1/AC)   [static](http://www.mamicode.com/so/1/static)   [没有](http://www.mamicode.com/so/1/没有)   [vue](http://www.mamicode.com/so/1/vue)   [文件夹](http://www.mamicode.com/so/1/文件夹)   [pac](http://www.mamicode.com/so/1/pac)   [bpa](http://www.mamicode.com/so/1/bpa)   [传递](http://www.mamicode.com/so/1/传递)   

用props传递一张图片的src给子组件，发现在子组件中根本加载不到图片，打开控制台，发现img的src并没有被解析成正确的地址

经过研究发现，如果图片是在static文件夹下，可以直接传递，如果在assets文件夹下，是需要require传入的。否则webpack解析不到正确的路径

具体解释：https://blog.csdn.net/zgh0711/article/details/79712540

[vue 通过props传递图片src给子组件](http://www.mamicode.com/info-detail-2328296.html)

标签：[http](http://www.mamicode.com/so/1/http)   [AC](http://www.mamicode.com/so/1/AC)   [static](http://www.mamicode.com/so/1/static)   [没有](http://www.mamicode.com/so/1/没有)   [vue](http://www.mamicode.com/so/1/vue)   [文件夹](http://www.mamicode.com/so/1/文件夹)   [pac](http://www.mamicode.com/so/1/pac)   [bpa](http://www.mamicode.com/so/1/bpa)   [传递](http://www.mamicode.com/so/1/传递)   

原文地址：https://www.cnblogs.com/lijianjian/p/9153287.html

父组件传入图片路径和路由给子组件: https://blog.csdn.net/zgh0711/article/details/79712540

**二十四:** vue实现跳转浏览器新的[标签页](https://www.jianshu.com/p/7ad62f3e36dd)

window.[open(](https://zhidao.baidu.com/question/200963962.html))

```js
 window.opener = null
 window.open('', '_parent')
 window.close()


```

二十五: **vxe-table**

[开发指南](https://xuliangzhan.github.io/vxe-table/#/table/edit/rowDisable)

二十六: iview 列([内容自**定义**)](https://blog.csdn.net/qq_41725450/article/details/90054676)

例如(文档中心文件夹的权限)

二十七: **二叉树**

js构建二叉树

```js
class TreeNode {
      constructor (value) {
        this.value = value
        this.left = null
        this.right = null
      }
      printTheTree () {
        console.log(
            `root value is ${this.value}, left child is ${JSON.stringify(this.left)},              right child is ${JSON.stringify(this.right)}`
        )
      }
    }
    const node3 = new TreeNode(3)
    const node1 = new TreeNode(1)
    const node6 = new TreeNode(6)
    const node4 = new TreeNode(4)
    const node7 = new TreeNode(7)
    
    node3.left = node1
    node3.right = node6
    node6.left = node4
    node6.right = node7
    node3.printTheTree()
```

1: **前序遍历**

根节点 => 左子树 => 右子树

问题: 给定一个二叉树，返回它的 *前序* 遍历。

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var preorderTraversal = function(root) {
    if (!root) return [];
    var result = []
    result.push(root.val)
    result = result.concat(preorderTraversal(root.left))
    result = result.concat(preorderTraversal(root.right))
    return result
};

```

2: **中序遍历**

左子树 => 根节点 => 右子树

对于二叉树:可以通过中序遍历得到一个递增的有序数列

3: **后序遍历**

左子树 =>  右子树 => 根节点

删除树节点时,删除过程是按照后序顺序删除,左子树=>右子树=>节点本身

二十八: [SCSS](https://blog.csdn.net/KimBing/article/details/89738636)

二十九: 百分数与小数[互相转换](https://blog.csdn.net/weixin_40829761/article/details/80685168)

```js
  //百分数转化为小数
		//1.先去掉百分号
		//2.再除以100
		//3.返回出去
		
		var percent = "4.2%";//申明要放在函数前
		function toPoint(percent){
   		 	var str=percent.replace("%","");
    		        str= str/100;
   		 	return str;
		}
		toPoint(percent);
		var result = toPoint(percent);
		document.write(result);//0.042
		
		//小数转化为分数
		//1.先转化为number类型
		//2.再乘以100
		//3.保留小数位
		var point = 0.042;
		function toPercent(point){
			var percent = Number(point*100).toFixed(1);
			percent+="%";
			return percent;
		}
	  	 var result = toPercent(point);
		document.write("<br/>"+result);blog.csdn.net/weixin_40829761/article/details/80685168
```

百分数转小数: %替换成空,然后转为数字/100

小数转百分数: value * 100,+%

**三十:** js上舍入(天花板)下舍入(地板)

天花板: Math.ceil(1.5) 向上取整

栗子:  以上输出2

地板: Math.floor(1.5) 向下取整

栗子: 以上输出1

周围: Math.round(1.5) 就近取整(最接近的整数)  四舍五入取整

栗子: 以上输出2, 1.4输出1, 1.6 输出2

银行家舍入法: 四舍六入五考虑: 五后非空向前进,五后为空看奇偶,五前为偶即舍去五前为奇即进一

**三十一**: [状态码](https://blog.csdn.net/zhangmengleiblog/article/details/52513227)

**三十二:** npm [漏洞修复](https://blog.csdn.net/weixin_40817115/article/details/81007774)

- npm audit fix 控制台提示如下:

- ```js
  1 package update for 5 vulns involved breaking changes
    (use `npm audit fix --force` to install breaking changes; or do it by hand)
  ```

  

- npm audit fix --force 控制台提示如下：

  ```js
  added 199 packages from 111 contributors, removed 64 packages and updated 23 packages in 42.194sfixed 5 of 5 vulnerabilities in 1117 scanned packages
    1 package update for 5 vulns involved breaking changes
    (installed due to `--force` option)
  ```

  

- npm audit

```js
  === npm audit security report ===

found 0 vulnerabilities
 in 4598 scanned packages
```

修复完成

**npm audit fix**相关介绍详看链接

**三十三:** 微观宏观

**三十四:** 上传插件vue-simple-uploader

文档[链接地址](https://github.com/simple-uploader/vue-uploader/blob/master/README_zh-CN.md)

simple-uploader.js[链接地址](https://github.com/simple-uploader/Uploader/blob/develop/README_zh-CN.md)

用法示例[链接地址](https://www.jb51.net/article/122086.htm)

**三十五:** [虚拟dom](https://www.jianshu.com/p/af0b398602bc)原理

**三十六:** return & return false区别

详见[链接](https://blog.csdn.net/q3254421/article/details/83154247)

**三十七:** canvas 实现架构图

详见[链接](https://github.com/helinhui/web-record)

**三十八:**gitlab详细操作

[链接:](https://www.jianshu.com/p/fb61299086b6) 

**三十九**: [restful接口规范](https://blog.csdn.net/javamine/article/details/89640426)

**四十:** 日期[格式化](https://www.cnblogs.com/aaronthon/p/10640767.html)

**四十一:** 检测是[否是arr](https://www.cnblogs.com/lingdu87/p/9152806.html)

**四十二:** icon[报错](https://www.lanka.cn/2402_2402.html)

**四十三:** 数组的各种方法-是否改变原数组

1:  shift(): 将第一个数组删除, **返回删除的数组**,原数组改变

2: unshift(): 给数组前头加一个元素, **返回添加后的数组长度**,原数组改变

3: pop(): 删除数组最后一个元素, **返回被删除的元素**,原数组改变

4: push(item||Obj): 给数组末尾添加元素, **返回添加后的数组长度**,原数组改变

5: reverse(): 顺序翻转, **返回翻转过来的数组**,原数组改变

6: splice - 原数组改变

- splice(start,1, item)替换下标start的元素为item,返回被替换的元素
- splice(start,length)删除从start的开始的往后倒length位的元素,返回被删除的元素
- splice(start,length, item)从下标start开始往后数length位替换为item,返回被替换的元素

7: concat(array): 连接对个数组,返回新的数组,不改变原数组

8: join('字符'): 数字加入特定字符变为字符串,不改变原数组

9: slice(start,end): 返回选定的数组(从下标start开始的数组的第end位元素),不改变原数组

数组的方法: 

1: isArray():是否为数组

2: forEach(function): 遍历数组,

```js
const arr = [1, 2, 3, 4]
arr.forEach((item) => {
   console.log(item)// 1, 2, 3, 4
})
```

3: map(function): 通过指定函数处理数组的每个元素，并返回处理后的数组。

```js
const arr = [1, 2, 3, 4]
const a = arr.map((item) => {
  return item * 2
})
console.log(a) // [2, 4, 6, 8]
console.log(arr)// [1, 2, 3, 4]
```

4: filter(function): 筛选符合条件的数组项

```js
const arr = [1, 2, 3, 4]
const a = arr.filter((item) => {
  return item === 2
})
console.log(a)
console.log(arr)
```

5: reduce(function):  求出数组总和

```js
const arr = [1, 2, 3, 4]
const a = arr.reduce((total, item) => {
   return total + item
})
console.log(a) // 10
console.log(arr) // [1, 2, 3, 4]
```

6:  every(function):  检测数组中每一项是否符合条件,有一项不符合返回false

```js
const arr = [1, 2, 3, 4]
    const a = arr.every((item) => {
      return item === 2
    })
    console.log(a) // false
    console.log(arr) // [1, 2, 3, 4]
```

7: indexOf(item):判断数组中知否包含item,如果包含返回元素所在位置下标,反之返回-1

```js
// 存在
const arr = [1, 2, 3, 4]
const a = arr.indexOf(2)
console.log(a) // 1
console.log(arr) // [1, 2, 3, 4]

// 不存在
const arr = [1, 2, 3, 4]
const a = arr.indexOf(5)
console.log(a) // -1
console.log(arr) // [1, 2, 3, 4]
```

8: toString(): 数组转为字符串

```js
const arr = [1, 2, 3, 4]
const a = arr.toString()
console.log(a) // 1,2,3,4
console.log(arr) // [1, 2, 3, 4]
```

9: lastIndexOf(item): 返回item所在的最后的位置下标

```js
const arr = [1, 2, 3, 4, 2]
const a = arr.lastIndexOf(2)
console.log(a) // 4
console.log(arr) // [1, 2, 3, 4, 2]
```

**四十四:** 开发工具库[流程](https://juejin.im/post/5e958d0f6fb9a03c6675cb5d?utm_source=gold_browser_extension)

**四十五:** 

- echarts相关知识点梳理
- 1: x轴间隔上下显示,xAxis-data:["0","\n1","2","\n3","4","\n5","6"]
- 2:  x轴间隔斜着显示,xAxis-axisLabel: {interval: 0, rotate: 45}/*interval是间隔距离,rotate是斜角度数*/

**四十六:** npm run build 没有生成dist问题

config-index.js下的build配置,dist就是打包后生成的静态文件路径

```js
 index: path.resolve(__dirname, '../dist/index.html'),
 // Paths
 assetsRoot: path.resolve(__dirname, '../dist'),
 assetsSubDirectory: 'static',
 assetsPublicPath: '/',

```

**四十七**: vue项目优化-map文件

build执行之后dist-static-js文件里会有例如:1.js-1.js.map格式的文件,size很大

map是什么东东:

source map文件是js文件压缩后，文件的变量名替换对应、变量所在位置等元信息数据文件，一般这种文件和min.js主文件放在同一个目录下。 比如压缩后原变量是map，压缩后通过变量替换规则可能会被替换成a，这时source map文件会记录下这个mapping的信息，这样的好处就是说，在调试的时候，如果有一些JS报错，那么浏览器会通过解析这个map文件来重新merge压缩后的js,使开发者可以用未压缩前的代码来调试，这样会给我们带来很大的方便！**一句话，就是压缩的js与未压缩源文件js之间的映射关系文件。（就是一个桥梁）**

这玩意就是辅助我调试用的，正式站其实作用不大，而且处于安全考虑，可以直接干掉。

而这种还原性调试功能，目前**只有chorme才具有。**

解决: config-index.js下的build配置 = >**productionSourceMap: false,**

okay,打包之后,.map文件不见啦

**四十八:** iview select下拉问题,

描述: 后端返回的渲染name是这种格式: "测试-"前端项目"- 1",选中的时候获取不到对应id,无法选中

原因: 前端项目被认为是一个变量,故无法选中解决,去掉""就好

**四十九:** router-link和router-view的对应关系

router-link就相当于a标签: router-view相当于href;

router-link是to跳转的一个方式;

router-view用来渲染通过路由映射过来的组件，当路径更改时， 内容也会发生更改

router-link: tab选项卡中的头部选项router-view: tab选项卡的里的内容

**五十:** slot 插槽

vue里提供了一种将父组件的内容和子组件的模板整合的方法：内容分发，通过slot插槽来实现。

**五十一:** 虚拟dom原理

**五十二:** display;flex [用法](https://www.cnblogs.com/qingchunshiguang/p/8011103.html)

**五十三:** HTML5.2修改内容

1: dialog元素-默认隐藏,open属性显示,

- show() 相当于一个弹框
- showModal() 模态框,打开时不能操作背后页面的内容,

2: `rel="apple-touch-icon"`  可添加size属性

3: main标签,5.2之前,一个页面只有一个main标签,5.2开始,一个页面可有多个main标签,但是别的main标签要用hidden属性隐藏,display:none,visibility:hidden都不行,

```html
<main>...</main>
<main hidden>...</main>
<main hidden>...</main>
```

4: body内`<style>`,之前`<style>`仅在head中写,5.2 允许在 `<body>` 内使用 `<style>` 标签，就近定义结构样式。

- `<body>` 内的 `<style>` 可能会导致之前元素的布局改变，令页面发生重绘。所以尽量避免使用。

5: `<iframe>`添加 `allowpaymentrequest` 属性的方式，允许 `<iframe>` 内部网页使用  [Payment Request API](https://developer.mozilla.org/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)。

6: `legend` 5.2 之前，`<legend>` 中只能使用纯文本,5.2 开始可以使用标题元素了

```html
<form action="/action_page.php">
 <fieldset>
     < -- 5.2之前-- >
	<legend>Personalia:</legend>
     < -- 5.2-- >
    <legend><h2>Basic Information</h2></legend>
  </fieldset>
</form>
```

7: 移除特性

- `<keygen>`、`<menu>` 和 `<menuitem>` 元素
- 文本 `<input>` 的 `inputmode` 和 `dropzone` 属性
- `widow.showModalDialog()` 方法

8: 以下三类元素不能作为 `<p>` 段落的内容。

- 行内块、表格元素（Inline blocks、inline tables）
- 浮动元素（floated）
- 定位元素（positioned block-level elements）

9: **strict doctype**

HTML4 和 XHTML1 的严格文档类型声明（strict doctype）不再是有效 HTML。

