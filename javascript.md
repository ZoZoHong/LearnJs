#javascript
关键词
VAR.hasOwnProperty() 判断变量是否自身拥有该属性
console.log(x); 相当于打印
这里不喜欢用 == 而喜欢用 ===
天气免费api https://openweathermap.org/api
##判断
	与c语言一样
	if(...){
		;
	} else if(...){
		;
	} else {
		;
	}
##循环
1. for ( ; ; ) {

}
2. for (var key in o){

for (var i in arr){
    console.log('Hello,'+arr[i]+','+arr[i]);
}
	
} 用于遍历一个对象的所有属性
- for ... in 对array(数组)的循环得到的是string 而不是number.
3.while 
	while(){
		;
	}
	do {
	
	}while ();
##Map
Map 是一组键值对的结构,具有极快的查找速度.
e.g. 
- 
  var m = new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);
  m.get('Michael'); // 95
-	
ver m = ner Map(); 初始化一个map
m.set('str',number); 添加
m.has('str'); 判断是否存在
m.get('str'); 
m.delete('str'); 删除

##Set
Set和Map类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在Set中，没有重复的key。
关键: 不能重复
e.g. 
- var s = new Set([1, 2, 3, 3, '3']);
  s; // Set {1, 2, 3, "3"}
s.add(number);
s.delete();

##iterable 迭代

	遍历Array可以采用下标循环，遍历Map和Set就无法使用下标。为了统一集合类型，ES6标准引入了新的iterable类型，Array、Map和Set都属于iterable类型。

	具有iterable类型的集合可以通过新的for ... of循环来遍历。
 然而,更好的方式是直接使用iterable内置的forEach方法,它接收一个函数,每次叠氮全自动回调该函数.
 e.g. 
    var a = ['A','B','C'];
	a.name = 'Hello';
	for(var x of a){
		console.log(x); // A,B,C
	}
	for(var x in a){
		console.log(x); // 1,2,3,name
	}
	a.forEach(function (element, index, array) {
    // element: 指向当前元素的值
    // index: 指向当前索引
    // array: 指向Array对象本身  array set map
    console.log(element + ', index = ' + index);
});
Set 没有索引 所以 前两个参数都是元素本身 

s.forEach(function (element, sameElement, set) {
    console.log(element);
});
Map 的回调函数依次为 value key map;

var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
m.forEach(function (value, key, map) {
    console.log(value);
});
 
如果对某些参数不感兴趣，由于JavaScript的函数调用不要求参数必须一致，因此可以忽略它们。例如，只需要获得Array的element：

var a = ['A', 'B', 'C'];
a.forEach(function (element) {
    console.log(element);
});
 
 #函数
 定义函数 
 1. function abs(x)
    {
		if (typeof x !== 'number') {
        throw 'Not a number';
		}	//有时候要避免收到undefined,可以对参数进行检查
	    ...
	    return x;
    }
 2.匿名函数
   var abs = function(x)
   {
		...
		return x;
   };
    -
##arguments	 参数
JavaScript还有一个免费赠送的关键字arguments，它只在函数内部起作用，并且永远指向当前函数的调用者传入的所有参数。arguments类似Array但它不是一个Array：

##rest参数
由于JavaScript函数允许接收任意个参数，于是我们就不得不用arguments来获取所有参数	
 额外的参数
 function foo(a,b,...rest)
 {
	console.log('a =' + a);
	console.log('b =' + b);
	console.log(rest);
 }
 - 多余的参数以数组形式交给变量rest
 function sum(...rest) {
    var x = 0;
    for(var i=0;i<arguments.length;i++){
        x += rest[i];
    }
    console.log(x);
    return x;
}
##const 常量

##方法
在一个对象中绑定函数,成为这个对象的方法.
e.g.
var xiaoming = {
	name : 'xiaoming',
	birth : 1990,
	age : function(){
		var that = this; //捕获这个this
		var y = new Date().gerFullYear();
		return y - that.birth;
	}
};
xiaoming.age;
xiaoming.age(); //调用

注意这个this不一定每次都指向该对象.

##装饰器
利用 apply() 改变函数行为

e.g. 
var oldParseInt = parseInt;
window.parseInt = function(){
	count += 1;
	return oldParseInt.apply(null,arguments());
};
#高阶函数

## map / reduce
 map() 调用array的map()方法,传入我们自己的函数,就得到了一个新的array作为结果;
 reduce() array 进行累积
 使用前必须保证是array
 
 reduce练习
1.求积
	function product(arr){	
		function f(x,y) {
			return x*y;	
		}
		var result = arr.reduce(f);
		return result;
		}
	}
 2.str2int
	function string2int(s){
		var arr = s.split(''); //将字符串变成隔开
		arr = arr.map(function(x){
			return x-'0';
		});
	var result = arr.reduce(function(x,y){
		return 10*x+y;
	});    
	return result;
	}
 3.首字母大写,其他小写
	 function normalize(arr){
		return arr.map(function(x){
			return x[0].toUpperCase() + x.substr(1).toLowerCase();
		});
	 }
##filter 过滤
 true 留下 false 丢弃
 回调函数: filter()接收的回调函数，其实可以有多个参数。通常我们仅使用第一个参数，表示Array的某个元素。回调函数还可以接收另外两个参数，表示元素的位置和数组本身：
 ## sort
 
 ##array
 array.every() 每个函数是否符合
 array.find() 查找符合条件的第一个元素
 array.findIndex() 查找符合条件的第一个元素,返回索引,没找到返回-1
 array.forEach() 遍历数组
 
 
 #闭包
 在面向对象的程序设计语言里,比如java和c++,要在对象内部封装一个私有变量,可以用private修饰一个成员变量.
 在没有class机制,只有函数的语言里,借助闭包,同样可以封装一个私有变量.
 例:创建一个计数器:
 function create_counter(initial){
	var x = initial || 0;
	return {
		inc: function() {
			x += 1;
			return x;
		}
	}
 }
 var c1 = create_counter();
 c1.inc();
 
 #箭头函数
 就是简化版的匿名函数,并修复了this
 (argument) => ()
 
 #generator
 生成器
function* foo(x){
	yield x+1;
	yield x+2;
	return x+3;
}
yield用法
function* fib(max) {
    var
        t,
        a = 0,
        b = 1,
        n = 0;
    while (n < max) {
        yield a;
        [a, b] = [b, a + b];
        n ++;
    }
    return;
}
var f = fib(5);
f.next(); // {value: 0, done: false}
f.next(); // {value: 1, done: false}
f.next(); // {value: 1, done: false}
f.next(); // {value: 2, done: false}
f.next(); // {value: 3, done: false}
f.next(); // {value: undefined, done: true}
yield x 返回一个对象{},然后暂停
可以用 for...of 来迭代gengerator
 - 写成一个自增的id
 function next_id(){
	var number = 1;
	while(1) yield number++;
 }
#标准对象
 总结一下，有这么几条规则需要遵守：

不要使用new Number()、new Boolean()、new String()创建包装对象；

用parseInt()或parseFloat()来转换任意类型到number；

用String()来转换任意类型到string，或者直接调用某个对象的toString()方法；

通常不必把任意类型转换为boolean再判断，因为可以直接写if (myVar) {...}；

typeof操作符可以判断出number、boolean、string、function和undefined；

判断Array要使用Array.isArray(arr)；

判断null请使用myVar === null；

判断某个全局变量是否存在用typeof window.myVar === 'undefined'；

函数内部判断某个变量是否存在用typeof myVar === 'undefined'。

最后有细心的同学指出，任何对象都有toString()方法吗？null和undefined就没有！确实如此，这两个特殊值要除外，虽然null还伪装成了object类型。

更细心的同学指出，number对象调用toString()报SyntaxError：

123.toString(); // SyntaxError
遇到这种情况，要特殊处理一下：

123..toString(); // '123', 注意是两个点！
(123).toString(); // '123'
不要问为什么，这就是JavaScript代码的乐趣！
#RegExp 正则表达式
 用来匹配字符串的工具.
- \d 匹配一个数字 
- \w 匹配一个字母或数字
- .  匹配任意字符
- *  表示任意个字符
- +  至少一个字符
- ?  表示0或1个字符
- {n}   表示n个字符
- {n,m} 表示n-m个字符
- \s    匹配一个空格
- A|B   可以匹配A或B
- ^     表示行的开头
- ^\d   表示必须以数字开头.
- $     表示行的结束
- \d$   表示必须以数字结尾

var re1 = /ABC\-001/;
var re2 = new RegExp('ABC\\-001');
.test() 测试字符串是否符合
re.test('ABC-001');
re.test('ABC 001'); 
##切片字符串
'a b  c '.split(' ');
'a b  c  '.split(/\s+/);
'a,b, c  d '.split(/[\s\,]+/); 
! 如果用户输入一组标签,下次记得用正则表达式来把不规范的输入转化为正确的数组
##分组
exec()
e.g. 
- var re = /^(\d[3])-(\d[3,8]$)/;
re.exec('010-12345'); // '010-12345','010','12345'
匹配成功返回一个数组
var re = /^(0[0-9]|1[0-9]|2[0-3]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])$/;
re.exec('19:05:30'); // ['19:05:30', '19', '05', '30']

但对于日期
对于'2-30'，'4-31'这样的非法日期，用正则还是识别不了，或者说写出来非常困难，这时就需要程序配合识别了。

var re = /^\<(\w+\s\w+)\>\s(\w+\.?\w+\@\w+\.\w+$)/;
var r = re.exec('<Tom Paris> tom@voyager.org');
if (r === null || r.toString() !== ['<Tom Paris> tom@voyager.org', 'Tom Paris', 'tom@voyager.org'].toString()) {
    console.log('测试失败!');
}
else {
    console.log('测试成功!');
} 
# JSON
他是一种数据交换格式
UTF-8
为了统一解析，JSON的字符串规定必须用双引号""，Object的键也必须用双引号""。
number：和JavaScript的number完全一致；
boolean：就是JavaScript的true或false；
string：就是JavaScript的string；
null：就是JavaScript的null；
array：就是JavaScript的Array表示方式——[]；
object：就是JavaScript的{ ... }表示方式。
 
 ##序列化
 把一个对象序列化成json格式的字符串.
 JSON.stringfly(obj);
 JSON.stringfly(obj,null,'	'); 第二个参数是用于筛选键值,第3个是按什么样子输出
 此处是按缩进输出
 ##反序列化
 JSON.parse()
 把一个json格式的字符串,直接变成一个javascript对象
 
 
 #面对对象编程
JavaScript的面向对象编程和大多数其他语言如Java、C#的面向对象编程都不太一样。如果你熟悉Java或C#，很好，你一定明白面向对象的两个基本概念：

类：类是对象的类型模板，例如，定义Student类来表示学生，类本身是一种类型，Student表示学生类型，但不表示任何具体的某个学生；

实例：实例是根据类创建的对象，例如，根据Student类可以创建出xiaoming、xiaohong、xiaojun等多个实例，每个实例表示一个具体的学生，他们全都属于Student类型。

所以，类和实例是大多数面向对象编程语言的基本概念。
 
不过，在JavaScript中，这个概念需要改一改。JavaScript不区分类和实例的概念，而是通过原型（prototype）来实现面向对象编程。 
 
 学到创建对象(进度慢下来了
 
 
 
 
 
 
 
 
 
 
 
   