# ES6常见数组处理方法分析汇总

事先给出一个以下方法要遍历的数组对象：

```
    const arr = [
      {name:"黄药师",alias:"东邪",age:66},
      {name:"欧阳锋",alias:"西毒",age:66},
      {name:"段皇爷",alias:"南帝",age:76},
      {name:"洪七公",alias:"北丐",age:72},
      {name:"王重阳",alias:"中神通",age:80}
    ];
```

## 一、遍历数组元素进行某种逻辑判断返回布尔值的数组方法

### 1、array.every()

every方法用来检测数组中的每一项元素是否都通过了某一条件判断，通过则返回true，反之返回false
```
    const flag = arr.every(item => {
      return item.age === 66
    })
    console.log(flag)    //false
```

### 2、array.some()

some方法用来检测数组中是否存在至少一项元素满足某一条件判断，存在则返回true，反之则返回false

```
    const flag = arr.some(item => {
      return item.alias === "北丐"
    })
    console.log(flag)    //true
```

### 3、array.includes(element,fromIndex)

includes方法用来判断数组内是否包含某一个指定值，且可以指定从数组某一个索引值开始检索。其中element是要检索的元素，fromIndex是开始检索的索引值。

```
const flag = [1,2,3,5].includes(5,2);
console.log(flag)    //true
```

## 二、遍历数组元素并返回一个新数组

### 4、array.map()

map方法用来遍历数组中的每一个元素，然后对其做同一处理，返回新的元素最终组合成一个新数组返回。

```
    const arr1 = arr.map(item => {
      return {alias: `五绝之${item.alias}`}
    })
    console.log(arr1)  
    /* [{alias:"五绝之东邪"},{alias:"五绝之西毒"},{alias:"五绝之南帝"},{alias:"五绝之北丐"},{alias:"五绝之中神通"}] */
```

### 5、array.filter()

filter方法用来遍历数组中的每一项元素，然后执行同一判断条件的检测后过滤出满足条件的元素值最终组合成新的数组返回。

```
    const arr1 = arr.filter(item => {
      return item.name === "洪七公"
    })
    console.log(arr1); //[{name:"洪七公",alias:"北丐",age:72}]
```

## 三、数组处理的增删改查

### 6、array.pop()和array.shift()

pop方法用来删除数组的最后一个元素，并返回最后一个元素的值。备注：数组为空时则返回undefined

```
const newArr = [1,2,3,4,5];
const val = newArr.pop();
console.log(newArr);  //[1,2,3,4]
console.log(val);    //5
```

shift方法用来删除数组的第一个元素，并返回第一个元素的值。备注：数组为空时则返回undefined

```
const newArr = [1,2,3,4,5];
const val = newArr.shift();
console.log(newArr);  //[2,3,4,5]
console.log(val);    //1
```

### 7、array.push(element1,element2,...,elementN)和array.unshift(element1,element2,...,elementN)

push方法用来将一个或多个元素依次添加到数组的末尾，并返回新数组的长度。

```
    const arr = [1,2,3,4];
    const len = arr5.unshift(9,8);
    console.log(arr)  //[9,8,1,2,3,4]
    console.log(len)  //6
```
unshift方法用来将一个或多个元素依次添加到数组的开头，并返回新数组的长度。

```
    const arr = [1,2,3,4];
    const len = arr5.unshift(9,8);
    console.log(arr)  //[1,2,3,4,9,8]
    console.log(len)  //6
```

### 8、array.splice(startIndex,deleteItemNum,item1,item2,...,itemN)

splice方法可以实现对数组进行增删的操作并返回被删除的项所组成的数组，其中startIndex（必需）是规定要添加/删除元素的位置，若未负数则从末尾处开始；deleteItemNum是要删除的元素个数，若为0则不删除；itemN(非必需)为要新增的元素，插入位置即startIndex位置。

```
    const arr6 = [1,2,3,4,5,6,7];
    const result = arr6.splice(2,2,"a","b");
    console.log(arr6);     //[1,2,"a","b",5,6,7]
    console.log(result);   //[3,4]
    const result1 = arr6.splice(-2,1,"c");
    console.log(arr6);     //[1,2,"a","b",5,"c",7]
    console.log(result1);  //[6]
```

### 9、array.indexOf(element,fromIndex)和array.findIndex()

indexOf方法可以返回数组中匹配到的给定元素的第一个索引值，若不存在则返回-1。其中element是要匹配的指定元素，fromIndex为开始执行匹配检索的索引位置。

```
const idx = [1,2,3,4,5].indexOf(6);
const idx1 = arr.indexOf({name:"洪七公",alias:"北丐",age:72}
)
console.log(idx);   //-1
console.log(idx1);   //-1   我们发现对于复杂的对象数组，indexOf是无法进行索引位置查找的
```

findIndex方法与indexOf方法的作用类似，但更高级，一般用来处理一些复杂的对象数组，查找到则返回第一个匹配元素的索引，反之则返回-1.

```
const idx = arr.findIndex(item => {
  return item.name === "洪七公"
})
console.log(idx)   //3
```
## 数组的其他处理方法

### 10、array.reverse()

reverse方法用来翻转原数组的先后顺序

```
const arr = [1,2,3,4,5];
arr.reverse();
console.log(arr)  //[5,4,3,2,1]
```

### 11、array.join()

join方法用来将数组中的各项元素用某一指定的字符串进行拼接，返回一个新的字符串。

```
cosnt arr = [1992,01,12];
arr.join("-");
console.log(arr)   //"1992-01-12"
```


### 12、array.concat(arr1,arr2,...,arrN)

concat为数组拼接方法，可将多个数组进行拼接，最终返回一个新数组，原数组没有改变。

```
const arr = [1,2];
const newArr = arr.concat(["a","b"],[9,8]);
console.log(newArr);    //[1,2,"a","b",9,8]
console.log(arr);       //[1,2]
```

### 13、array.sort([copareFunction])

sort方法可以对数组按某一指定比较规则进行排序。如果不传参数则按照字符编码的顺序进行排序

### 14、array.reduce(function(prev,cur,indedx,arr),initialValue)

reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。一般来说空数组是不会进行回调的，用空数组执行reduce方法时会报错，但如果设置了初始值则可以避免，但一般也不推荐(因为没有意义)。

initialValue是可自定义的初始值，如果设置了则以其作为初始值（此时起始所以为0），如果不设置则以数组的第一个元素作为初始值（此时起始索引为1）。如下面的2个累加计算示例可看出来
```
    const arr = [1,2,3,4]
    const val = arr.reduce((prev,cur,index,arr) => {
      console.log(index)  //依次为1,2,3
      return prev + cur;
    })
    console.log(val)  //10
```

```
    const arr = [1,2,3,4]
    const val = arr.reduce((prev,cur,index,arr) => {
      console.log(index)  //依次为0,1,2,3
      return prev + cur;
    })
    console.log(val)  //10
```

reduce方法可以说是一个高级方法，因为他的可自定义的累加器函数，可以处理很多比较高级的操作，常见的有：

#### 数组去重

```
let arr = [1,2,3,3,1,2]
let newArr = arr.reduce((pre,cur)=>{
    if(!pre.includes(cur)){
      return pre.concat(cur)
    }else{
      return pre
    }
},[])
console.log(newArr);// [1, 2, 3]
```

#### 计算数组中各元素出现的次数

```
let characters = ['a', 'b', 't', 't', 'a','f'];

let arr = characters.reduce((pre,cur)=>{
  if(cur in pre){
    pre[cur]++
  }else{
    pre[cur] = 1 
  }
  return pre
},{})
console.log(arr); //{a: 2, b: 1, t: 2, f: 1}
```

#### 对象数组中的单个属性累加

```
const achievement = [
  {year:'2016年',number: 231200},
  {year:'2017年',number: 201900},
  {year:'2018年',number: 275678},
  {year:'2019年',number: 301200}
];
const sum = achievement.reduce((prev,cur) => {
  return prev + cur.number
},0)
console.log(sum)  //1009978
```

#### 将二维数组转化为一维数组

```
let arr = [[0, 1], [2, 3], [4, 5]]
let newArr = arr.reduce((pre,cur)=>{
    return pre.concat(cur)
},[])
console.log(newArr); // [0, 1, 2, 3, 4, 5]
```

#### 将多维数组转化为一维数组

```
let arr = [[0, 1], [2, 3], [4,[5,6,7]]]
const newArr = function(arr){
   return arr.reduce((pre,cur)=>pre.concat(Array.isArray(cur)?newArr(cur):cur),[])
}
console.log(newArr(arr)); //[0, 1, 2, 3, 4, 5, 6, 7]
```