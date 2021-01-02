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
let obj = {name:'frank'} //name是字符串；
obj.name = 'frank' // name 是字符串；
obj['name'] = 'frank';
obj['na'+'me'] = 'wanti;
let key = 'name'; obj[key] = 'wanti';



无法通过自身修改或增加共有属性：
let obj ={},obj2 = {} //共有toString;
obj.toString = 'xxx' 只会更改obj自身属性；
obj2.toString还是在原型上
```

****


