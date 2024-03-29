# js-knowledge（前端js知识点总结）

## JavaScript中如何检测一个变量是一个String类型？请写出函数实现

方法1
```js
function isString(obj){
    return typeof(obj) === "string"? true: false;
    // returntypeof obj === "string"? true: false;
}
```
方法2
```js
function isString(obj){
    return obj.constructor === String? true: false;
}
```
方法3
```js
function isString(obj){
     return Object.prototype.toString.call(obj) === "[object String]"?true:false;
}
如：
var isstring = isString('xiaoming');
console.log(isstring);  // true
```
## 请用js去除字符串空格？
方法一：使用replace正则匹配的方法
```js
去除所有空格: str = str.replace(/\s*/g,"");      
去除两头空格: str = str.replace(/^\s*|\s*$/g,"");
去除左空格： str = str.replace( /^\s*/, “”);
去除右空格： str = str.replace(/(\s*$)/g, "");
str为要去除空格的字符串，实例如下：
var str = " 23 23 ";
var str2 = str.replace(/\s*/g,"");
console.log(str2); // 2323
```
方法二：使用str.trim()方法
```js
str.trim()局限性：无法去除中间的空格，实例如下：
var str = "   xiao  ming   ";
var str2 = str.trim();
console.log(str2);   //xiao  ming 
同理，str.trimLeft()，str.trimRight()分别用于去除字符串左右空格
```
## 你如何获取浏览器URL中查询字符串中的参数？
```js
测试地址为：http://www.runoob.com/jquery/misc-trim.html?channelid=12333&name=xiaoming&age=23
function showWindowHref(){
    var sHref = window.location.href;
    var args = sHref.split('?');
    if(args[0] == sHref){
        return "";
    }
    var arr = args[1].split('&');
    var obj = {};
    for(var i = 0;i< arr.length;i++){
        var arg = arr[i].split('=');
        obj[arg[0]] = arg[1];
    }
    return obj;
}
var href = showWindowHref(); // obj	
console.log(href['name']); // xiaoming
```
## 判断一个字符串中出现次数最多的字符，统计这个次数
```js
var str = 'asdfssaaasasasasaa';
var json = {};
for (var i = 0; i < str.length; i++) {
    if(!json[str.charAt(i)]){
       json[str.charAt(i)] = 1;
    }else{
       json[str.charAt(i)]++;
    }
};
var iMax = 0;
var iIndex = '';
for(var i in json){
    if(json[i]>iMax){
         iMax = json[i];
         iIndex = i;
    }
}        
console.log('出现次数最多的是:'+iIndex+'出现'+iMax+'次');
```
## js 字符串操作函数
```js
concat() – 将字符串或者数组组合起来，返回一个新的字符串。
indexOf() – 返回字符串中一个子串第一处出现的索引。如果没有匹配项，返回 -1 。
charAt() – 返回指定位置的字符。
lastIndexOf() – 返回字符串中一个子串最后一处出现的索引，如果没有匹配项，返回 -1 。
match() – 检查一个字符串是否匹配一个正则表达式。
substr() 函数 -- 返回从string的startPos位置，长度为length的字符串
substring() – 返回字符串的一个子串。传入参数是起始位置和结束位置。
slice() – 提取字符串的一部分，并返回一个新字符串。
replace() – 用来查找匹配一个正则表达式的字符串，然后使用新字符串代替匹配的字符串。
search() – 执行一个正则表达式匹配查找。如果查找成功，返回字符串中匹配的索引值。否则返回 -1 。
split() – 通过将字符串划分成子串，将一个字符串做成一个字符串数组。
length – 返回字符串的长度，所谓字符串的长度是指其包含的字符的个数。
toLowerCase() – 将整个字符串转成小写字母。
toUpperCase() – 将整个字符串转成大写字母。
```
## Array 对象方法
```js
concat() 连接两个或更多的数组，并返回结果。 // arr.concat(arr2)
join() 把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。 arr.join(',')
pop() 删除并返回数组的最后一个元素。  
var arr = [2,3,4,5];var arr2 = arr.pop();
console.log(arr2); // 删除的数组的最后一个元素为：5
console.log(arr);  // 删除元素之后的数组为：[2, 3, 4]
shift() 删除并返回数组的第一个元素
var arr = [2,3,4,5];var arr2 = arr.shift();
console.log(arr2); // 删除的数组的第一个元素为：2
console.log(arr);  // 删除元素之后的数组为：[3, 4，5]
push() 向数组的末尾添加一个或更多元素，并返回新的长度。
var arr = [2,3,4,5];var arr2 = arr.push(6);
console.log(arr2);  // 返回的数组长度：5 
console.log(arr);  // [2, 3, 4, 5, 6]
unshift() 向数组的开头添加一个或更多元素，并返回新的长度。
var arr = ['xiao','ming','qiqi','aiming'];var arr1 = arr.unshift('lang');
console.log(arr1);  // 返回的数组的长度：  5
console.log(arr);  //向数组开头添加元素返回的结果：["lang", "xiao", "ming", "qiqi", "aiming"]
reverse() 颠倒数组中元素的顺序。
var arr = [2,3,4,5];
arr.reverse();
console.log(arr);   //  [5, 4, 3, 2]
slice() 从某个已有的数组返回选定的元素
var arr = [2,3,4,5];var arr2 = arr.slice(1,3);
console.log(arr2);  // 截取区间返回的数组为：[3, 4]
console.log(arr);  // [2, 3, 4, 5]
sort() 对数组的元素进行排序
splice() 删除元素，并向数组添加新元素。
toSource() 返回该对象的源代码。
toString() 把数组转换为字符串，并返回结果。
toLocaleString() 把数组转换为本地数组，并返回结果。
```
## 编写一个方法 去掉一个数组的重复元素
```js
方法一：
var arr = [0,2,3,4,4,0,2];
var obj = {};
var tmp = [];
for(var i = 0 ;i< arr.length;i++){
   if( !obj[arr[i]] ){
      obj[arr[i]] = 1;
      tmp.push(arr[i]);
   }
}
console.log(tmp);
结果如下： [0, 2, 3, 4]
 方法二：
var arr = [2,3,4,4,5,2,3,6],
   arr2 = [];
for(var i = 0;i< arr.length;i++){
    if(arr2.indexOf(arr[i]) < 0){
        arr2.push(arr[i]);
    }
}
console.log(arr2);
结果为：[2, 3, 4, 5, 6]
 方法三：
var arr = [2,3,4,4,5,2,3,6];
var arr2 = arr.filter(function(element,index,self){
return self.indexOf(element) === index;
});
console.log(arr2);
结果为：[2, 3, 4, 5, 6]
```
## 求数组的最值？
方法一：求数组最大值：Math.max.apply(null,arr);
```js
var arr = [3,43,23,45,65,90];
var max = Math.max.apply(null,arr);console.log(max);// 90
```
求数组最小值：Math.min.apply(null,arr);
```js
var arr = [3,43,23,45,65,90];
var min = Math.min.apply(null,arr);console.log(min);// 3
```
方法二：Array.max = function(arr){} / Array.min = function(arr){}
```js
var array = [3,43,23,45,65,90];
Array.max = function( array ){ 
   return Math.max.apply( Math, array );
};
Array.min = function( array ){ 
   return Math.min.apply( Math, array );
};
var max = Array.max(array);console.log(max);  // 90
var min = Array.min(array);console.log(min);  // 3
```
方法三：Array.prototype.max = function(){};Array.prototype.min = function(){};

求数组最大值(基本思路：将数组中的第一个值赋值给变量max ,将数组进行循环与max进行比较，将数组中的大值赋给max,最后返回max;)
```js
var arr = [3,43,23,45,65,90];
Array.prototype.max = function() { 
    var max = this[0];
    var len = this.length; 
    for (var i = 0; i < len; i++){ 
        if (this[i] > max) { 
          max = this[i]; 
        } 
    } 
    return max;
}
var max = arr.max();
console.log(max);  // 90
```
求数组最小值：
```js
var arr = [3,43,23,45,65,90];
Array.prototype.min = function() { 
    var min = this[0];
    var len = this.length;
    for(var i = 0;i< len;i++){
        if(this[i] < min){
            min = this[i];
        }
    }
    return min;
}
var min = arr.min();console.log(min);  // 3
```
## 数组排序相关
数组由小到大进行排序：sort,sortnum
```js
var arr = [3,43,23,45,65,90];
function sortnum(a,b){
　　return a-b;
}
arr = arr.sort(sortnum);
console.log(arr);
```
// [3, 23, 43, 45, 65, 90]
数组由大到小进行排序：sort,sortnum;
```js
var arr = [3,43,23,45,65,90];
function sortnum(a,b){
　　return b-a;
}
arr = arr.sort(sortnum);
console.log(arr);
// [90, 65, 45, 23, 43, 3]
```
数组的翻转
方法一：
```js
var arr = [1,2,3,4];
var arr2 = [];
while(arr.length) {
    var num = arr.pop(); //删除数组最后一个元素并返回被删除的元素
    arr2.push(num);
}
console.log(arr2);
// [4, 3, 2, 1]
```
方法二：
```js
var arr = [1,2,3,4];
var arr2 = [];
while(arr.length){
    var num = arr.shift(); //删除数组第一个元素并返回被删除的元素
    arr2.unshift(num);
}
console.log(arr2);
```
## $(this) 和 this 关键字在 jQuery 中有何不同？
```html
$(this) 返回一个 jQuery 对象，你可以对它调用多个 jQuery 方法，比如用 text() 获取文本，用val() 获取值等等。
而 this 代表当前元素，它是 JavaScript 关键词中的一个，表示上下文中的当前 DOM 元素。你不能对它调用 jQuery 方法
直到它被 $() 函数包裹，例如 $(this)。
```
## jquery怎么移除标签onclick属性？
```html
获得a标签的onclick属性: $("a").attr("onclick")
删除onclick属性：$("a").removeAttr("onclick");
设置onclick属性：$("a").attr("onclick","test();");
```
## jquery中addClass,removeClass,toggleClass的使用。
```html
$(selector).addClass(class)：为每个匹配的元素添加指定的类名
$(selector).removeClass(class)：从所有匹配的元素中删除全部或者指定的类，删除class中某个值；
$(selector).toggleClass(class)：如果存在（不存在）就删除（添加）一个类
$(selector).removeAttr(class);删除class这个属性；
```
## jQuery中的Delegate()函数有什么作用？
```html
 delegate()会在以下两个情况下使用到：
 如果你有一个父元素，需要给其下的子元素添加事件，这时你可以使用delegate()了，代码如下：
$("ul").delegate("li", "click", function(){ $(this).hide(); });
```
## Ajax的优缺点及工作原理？
```html
优点
1.减轻服务器的负担,按需取数据,最大程度的减少冗余请求
2.局部刷新页面,减少用户心理和实际的等待时间,带来更好的用户体验
3.基于xml标准化,并被广泛支持,不需安装插件等,进一步促进页面和数据的分离
缺点
1.AJAX大量的使用了javascript和ajax引擎,这些取决于浏览器的支持.在编写的时候考虑对浏览器的兼容性.
2.AJAX只是局部刷新,所以页面的后退按钮是没有用的.
3.对流媒体还有移动设备的支持不是太好等
```
