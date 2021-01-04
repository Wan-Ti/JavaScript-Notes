# JavaScript Notes

**七种数据类型**

Nmuber | String | Bool |  Symbol |  Null | Undefined  |  Object

**五个falsy值**

Null | Undefined | 0 | NaN | " " (空字符串)

### 对象 Object

**定义**

1.无需的数据集合；</br>
2.键值对的集合;</br>

**写法**

```
let obj = { 'name':'wanti','age': 18 };
let obj = new Object({'name':'wanti'});
console.log({ 'name':'frank','age':18});
```

**细节**

1.键名是字符串，不是标识符，可以包含任意字符</br>
2.引号可省略，省略之后就只能写标识符</br>
3.即便引号省略，键名依旧是字符串</br>

### 属性名

**每个key都是对象的属性名(property)**;

**每个value都是对象的属性值**；

**变量作属性名**

```
let p1 = 'name';
let obj={p1:'wanti'};/* 属性名则为'p1' */
let obj={[p1]:'wanti'};/* 属性名则为'name' */
```
对比：</br>
1. 不加[]的属性名会自动变成字符串;</br>
2. 加了[]则会当作变量求值；</br>
3. 值如果不是字符串，则会自动变成字符串；

**对象的隐藏属性**

1. JS中的每一个对象都有一个隐藏属性</br>
2. 该隐藏属性储存着其共有属性组成的对象的地址</br>
3. 这个共有属性组成的对象叫做原型</br>
4. 即：隐藏属性储存着原型的地址</br>


### 增删改查

**删除属性**

```
delete obj.xxx或delete obj['xxx']
1. 即可删除obj的xxx属性；
2. 区分[属性值为undefined]和[不含属性名]

不含属性名：
'xxx' in obj === false;

含有属性名，但是值为undefined：
'xxx' in obj && obj.xxx === undefined

注意obj.xxx ==== undefined:
不能断定'xxx'是否为obj的属性

```

**查看(读取)所有属性**

```
查看自身所有属性：
Object.keys(obj;

查看自身+共有属性：
console.dir(obj);
或者依次用Object.key打印出obj.__proto__;

判断一个属性是自身的还是共有的：
obj.hasOwnProperty('toString')
```

**修改或增加属性**

```
直接赋值：
let obj = {name:'wanti'} //name是字符串；
obj.name = 'wanti' // name 是字符串；
obj['name'] = 'wanti';
obj['na'+'me'] = 'wanti;
let key = 'name'; obj[key] = 'wanti';
/* obj.key等价于obj['key'] */;

批量赋值：
Object.assign(obj,{age:18,gender:'female'})

无法通过自身修改或增加共有属性：
let obj ={},obj2 = {} //共有toString;
obj.toString = 'xxx' 只会更改obj自身属性；
obj2.toString还是在原型上

强制修改或增加(非常不建议修改原型，因为这回引起很多问题，除非你有能力解决这些问题)：
obj.__proto__.toString = 'XXX' // 不推荐使用—__proto__ ;
Object.prototype.toString = 'xxx';

修改隐藏属性：
推荐使用：
let obj = Object.create(common);
obj.name = 'wanti';
ley obj2 = Object.create(common);
obj2.name = 'jack'

不推荐使用__proto__:
let obj = {name:'wanti'}; 
let obj2 = {name: 'jack'};
let common = {kind:'human'};
obj.__proto__ = common;
obj2.__proto__ = common;

```

原型--每个对象都有原型：
```
原型里存着对象的共有属性；
比如obj的原型就是一个对象；
obj.__proto__存着这个对象的地址；
这个对象里有toString/constructor/valueOf等属性
```

原型--对象的原型也是对象

    · 所以对象的原型也有原型；
    · obj = {}的原型即为所有对象的原型；
    · 这个原型包括所有对象的共有属性，是对象的根；
    · 这个原型也有原型，是null;

**查看属性**

```
中括号语法：obj['key'];// 优先使用
点语法：obj.key;
```

**必须搞懂这一题**

```
代码：
let list = ['name', 'age' , 'gender']
let persion = {
	name:'wanti',age:18,gender:'woman'
}

for(let i = 0 ;i<list.length;i++){
	let name = list[i]
    console.log(peison__??__)
}
使得person的所有属性被打印出来；
```

```
选项：
1.console.log(person.name);
2.console.log(person[name])
```

## 语法

**表达式与语句**

区别(非绝对)：

    · 表达式一般都有值，语句可能有也可能没有；
    · 语句一般会改变环境(声明、赋值)

大小写敏感：

    · var a 和var A 是不同的；
    · object和Object是不同的；
    · function和Function是不同的；

大部分空格无实意，唯独return后年不能加return；

**标识符**

规则：</br>
第一个字符可以是Unicode字母或$或_或中文；</br>
第二个字符除了上述还可以有数字；

变量名是标识符：
```
var _ = 1;
var $ = 2;
var _____=6;
var 你好 = 'hi'

```

**if语句**

语法：</br>
if(表达式){语句1}else{语句2}

面试题：
```
a = 1;
if( a === 2 )
	console.log('a');
    console.log('a等于2’)；
```

推荐写法：
```
if (表达式) {
  语句
} else if (表达式) {
  语句
} else {
  语句
}
```

次推荐：
```
function fn () {
  if (表达式) {
     return  表达式
  }
  if (表达式) {
    return  表达式
  }
  return  表达式
}

```



**switch语句**

语法：
```
switch (fruit) {
  case "apple":
     ...
  break;
  case "apple":
     ...
  break;
  default:
      ...
}

/*大部分的时候如果省略break你就完了，因为这样会陷入死循环*/
     
```

**问号冒号表达式**

表达式1:表达式2:表达式3

**while循环**

语法：</br>
while(表达式){ 语句 }</br>
判断表达式的真假;</br>
当表达式为真，执行语句，执行完再判断表达式的真假；</br>
当表达式为假，执行后面的语句；</br>

**for循环**

for是while循环的方便写法。

语法：</br>
for (语句1；表达式2；语句3){
	循环体
}

break和continue的区别是：</br>
break是退出所有循环，而continue是退出当前循环；

**label语句**

语法：
```
foo :{
   console.log(1);
   break foo;
   console.log('本行不会输出');
}
console.log(2)

题目：
{
   foo: 1
}
```
解释这段代码

## 数据类型和运算符

**七种数据类型**

    · 数字 number
    · 字符串 string
    · 布尔 bool
    · 符号 symbol
    · 空 undefined
    · 空 null
    · 对象 object

**字符串**

写法：
```
单引号：'hello'
双引号："hello"
反引号：`hello`
```

属性：
```
string.length:

'123'.length;//3
'\n\r\t'.length; // ?
''.length;// 0
' '.length;// 1


通过下标读取字符：
string[index]:
let s = "hello"
s[0] // "h";
s[5] // undefined;
s[4] // '0'

```

**undefined和null的区别**

区别：

    · 如果一个变量声明了，但没有赋值，那么它的默认值就是undefined，而非null;
    · 如果一个函数，没有写return，那么默认 return undefined，而不是null；
    · 习惯上会将非对象的空值写为undefined，将对象的空值写为null;
    
**变量声明**

三种声明变量：
```
var a = 1;// 过时的、不好用的
let a = 1;// 新的，更合理的
const a = 1;//声明时必须赋值，且不能再改；
a = 1;// 错误的！！！不许这样写！！
```

let 声明规则：

    · 遵循块作用域，即适用范围不能超出{};
    · 不能重复声明；
    · 可以赋值，也可以不赋值；
    · 必须先声明再使用，否则会报错；
    · 全局声明的 let 变量，不会变成window的属性；
    · for 循环配合 let 有奇效；
    
const 声明规则：</br>
与let几乎一样，唯独不一样的是const声明时就要赋值，且赋值后不能更改；

**数据类型之间的转换**

```
number => string :
String(n);
n + '';

string => number:
Number(s);
parseInt(s) / parseFloat(s);
s - 0 ;

x => bool:
Boolean(x);
!!x;

x => string:
String(x);
x.toString()

```
  
## JS对象分类

**new操作符**

new X()的作用：


    · 自动创建空对象</br>
    · 自动为空对象关联原型，原型地址指定为X。prototype;
    · 自动将空对象作为this关键字运行构造；
    · 自动return this;
构造函数X：</br>
X函数本身负责给对象本身添加属性；</br>
X.prototype对象负责保存对象的共用属性；

结论：</br>
你是谁构造的，你的原型就是谁的prototype属性对应的对象；

公式：</br>
对象.__proto__===其构造函数.prototype;</br>

计算机中对象分类的必要性类似于生物学科中给生物进行分类一样；

**数组对象**

定义一个数组：
```
let arr =[1,2,3];
let arr = new Array(1,2,3) // 元素为1，2，3；
let arr = new Array(3) // 长度为3；
```

数组对象的自身属性：</br>
'0' / '1' / '2' /'length';</br>
属性名没有数字，只有字符串；

**函数对象**

定义一个函数：
```
function fn(x,y) { return x+y}
let fn2 = function fn(x,y) { return x+y}
let fn = (x,y) => x+y;
let fn = new Function('x','y','return x+y');
```

函数对象自身属性：</br>
'name' / 'length';

函数对象公用属性：</br>
'call' / 'apply' / 'bind';


**数组对象**

创建一个数组
```
新建：
let arr = [1,2,3];
let arr = new Array(1,2,3);
let arr = new Array(3);

转化：
let arr = '1,2,3'.split(',');
let arr = '123'.splite('');
Array.from('123');

伪数组：
let divList = document.querySelectorAll('div');
伪数组的原型链中并没有数组的原型；

合并两个数组，得到新数组：
arr1.concat(arr2);

截取一个数组的一部分：
arr1.slice(1) //从第二个元素开始；
arr1.slice(0) //全部截取；
JS只提供了浅拷贝；
```

删除元素：
```
跟对象一样：
let arr = ['a','b','c'];
delete arr['0'];
arr //[empty,'b','c'];

删除头部元素：
arr.shift() //arr被修改，并返回被删除元素；

删除尾部元素：
arr.pop() //arr被修改，并返回被删除元素；

删除中间元素：
arr.splice(index,1) //删除index的一个元素；
arr.splice(index,1,'x') //并在删除位置添加X
arr.splice(index,1,'x','y') //并在删除位置添加'x','y'
```

查看所有元素：
```
查看所有属性名：
let arr = [1,2,3,4,5];arr.x='xxx';
Object.keys(arr);
for(let key in arr){console.log(`${key}:${arr[key]}`)};

查看数字(字符串)属性名和值：
for(let i = 0;i < arr.length;i++){
  console.log(`${i}: ${arr[i]}`)
}

需要自己写forEach才能理解forEach:
function forEach(array,fn){
  for (let i =0;i < array.length;i++){
    fn(array[i], i, array)
  }
}
forEach用for访问array的每一项
```

查看单个属性：
```
与对象一样：
let arr = [111,222,333];
arr[0];

索引越界：
arr[arr.length] === undefined;
arr[-1] === undefined;

查找某个元素是否在数组里：
arr.indexOf(item) //存在返回索引，否在返回-1；

使用条件查找元素：
arr.find(item => item % 2 === 0)//找第一个偶数

使用条件查找元素的索引：
arr.findIndex(item => item % 2 === 0)//找第一个偶数的索引
```

增加数组中的元素
```
在尾部增加元素：
arr.push(newItem) //修改arr,返回新长度；
arr.push(item1,item2)//修改arr,返回新长度

在头部增加元素：
arr.unshift(newItem) //修改arr,返回新长度；
arr.unshift(item1,item2) //修改arr,返回新长度

在中间增加元素：
arr.splice(index,0,'x')//在index处插入'x'
arr.splice(index,0,'x','y')
```

修改数组中的元素：
```
反转顺序：
arr.reverse() //修改原数组

自定义顺序：

arr.sort((a,b) => a-b)
```
