**一、检测数组**

_1、instanceof_
```
if(value instanceof Array) {
//对数组进行某些操作
}
```

_2、isArray_
```
if(Array.isArray(value)) {
//对数组进行某些操作
}
```

**二、转换方法**

所有对象都具有toLocaleString()、toString()和valueOf()方法。

_1、调用toString()方法会返回由数组中每个值的字符串形式拼接而成的一个以逗号分隔的字符串。_

_2、调用valueOf()返回的还是数组。_

_3、调用toLocaleString()方法会返回由数组中每个值的字符串形式拼接而成的一个以逗号分隔的字符串。_

实际上，为了创建这个字符串会调用数组每一项的toString()方法。
```
var colors = ["red", "blue", "green"]; //创建一个包含3个字符串的数组
alert(colors.toString()); //colors,blue,green
alert(colors.valueOf()); //colors,blue,green
alert(colors); //colors,blue,green
```
第一个alert毫无疑问是返回以逗号分隔的字符串。第二和第三个最后再浏览器的警告框中也返回的是以逗号分隔的字符串，原因在于alert要接收字符串参数，所以它会再后台调用toString方法。valueOf()还是返回数组的。

**三、栈方法（LIFO  Last-in-First-Out 后进先出）**

1、push 数组末尾推入，返回修改后数组的长度

2、pop 数组末尾删除，返回当前删除的项

**四、队列方法(FIFO First-in-First-Out 先进先出)**

1、push 数组末尾推入，返回修改后数组的长度

2、shift 删除数组第一项，返回当前删除的项


unshift 从数组的前端加项。返回新数组的长度。与pop结合使用可以从相反方向模拟队列，即在数组前端加项，从数组末尾移除项。

**五、重排序方法**

_1、reverse（）反转数组项的顺序。_

```
var values = [1,2,3,4];
values.reverse();
alert(values);         //5,4,3,2,1
```

_2、sort()_

默认情况按升序排列数组项---即最小的位于最前面，最大的位于最后面。
为了实现排序，sort()方法会调用数组每一项的toString()转型方法，然后比较得到的字符串，以确定如何排序。
即使数组中的每一项都是数值，sort()方法比较的也是字符串。

```
var values = [0,1,5,10,15];
values.sort();
alert(values);                 //0,1,10,15,5
```

sort()函数接收一个比较函数作为参数，比较函数接收两个参数

```
function compare(v1,v2){
     if(v1 < v2){                 //降序
       return -1;
     }else if(v1 > v2) {          //升序
       return 1;
     }else {
       return 0;
     }
}

或

function compare(v1, v2) {
    return v2-v1;
}
```

**六、操作方法**

_1、concat()_   

这个方法会先创建一个数组的副本，然后将接收到的参数添加到这个副本的末尾，最后返回新的数组。
在没有给该方法传递参数的情况，它只是复制当前数组并返回副本。如果传递从concat() 方法的是一或多个数组，则该方法会将这些数组中的每一项都添加到结果数组中。

如果传递的值不是数组，这些值会被简单地添加到结果数组的末尾。

```
var colors = ["red", "green", "blue"];
var colors2 = colors.concat("yellow", ["black", "brown"]);

alert(colors);           //red,green,blue
alert(colors2);          //red,green,blue,yellow,black,brown

```
_2、slice() （不会影响原始数组）_

它能够基于当前数组中的一或多个项创建一个新的数组。
slice()接受一或两个参数，即要返回项的起始和结束位置。
在只有一个参数的情况下，slice()方法返回从该参数指定的位置到当前数组末尾的所有项。
如果有两个参数，该方法返回起始和结束位置之间的项---但是不包括结束位置的项。

```
var colors = ["red", "green", "blue", "yellow", "purple"];
var colors2 = colors.slice(1);
var colors3 = colors.slice(1,4);

alert(colors2);           //green,blue,yellow,purple
alert(colors3);           //green,blue,yellow

```

_如果slice()方法参数中有一个负数，则用数组长度加上该数来确定相应的位置。如果结束位置小于歧视位置则返回空数组。_

_3、splice() (会改变原始数组)_

主要用途用向数组中插入项。

1、**删除**。可以删除任意数量的项，只需指定2个参数：要删除的第一项位置和要删除的项数。
例如： splice(0,2) 会删除数组中的前两项。

2、**插入**。可以向指定位置插入任意数量的项。只需提供3个参数：起始位置，0（删除0项），插入的项。如果插入多项，可以在传入第四第五以致任意多个项。
例如：`splice(2, 0, "red", "green")` 会从当前数组的位置2开始插入字符串 red 和 green。

3、**替换**。可以向指定位置插入任意项，且同时删除任意数量的项。只需指定3个参数：起始位置，删除的项数，插入的项（1或多个）。插入项与删除项不必相等。
例如： `splice(2, 1, "red", "green")`会从位置2开始删除1项，再从位置2开始插入字符串 red 和 green.

```
var colors = ["red", "green", "blue"];
var removed = colors.splice(0,1);               //删除第一项
alert(colors);                                  //red,green,blue
alert(removed);                                  //red

removed = colors.splice(1, 0, "yellow", "orange"); //从位置1开始插入 yellow 和 orange
alert(colors);                                     //green,yellow,orange,blue
alert(removed);                                      //返回空数组

removed = colors.splice(1, 1, "red", "purple");   //从位置1开始删除一项，并同时插入2项
alert(colors);                                    //green,red,purple,orange,blue
alert(removed);                                    //yellow       返回删除的项

```

_splice()方法始终返回一个数组，该数组包含数组中删除的项。（如果没有删除任何项，则返回空数组）_

**七、位置方法** 

indexOf()和lastndexOf(),这两个方法都接收两个参数：要查找的项和（可选）表示查找位置起点的索引。

1、indexOf()方法从数组开头（位置为0）开始向后查找。

2、lastIndexOf()方法则从数组的末尾开始向前查找。

这两个方法都返回要查找的项在数组中的位置，或者在没找到的情况下返回-1.再比较第一个参数与数组中的每一项时，会使用全等操作符；也就是要求查找的项必须严格相等（就像使用 ===一样）

例如：
```
var numbers = [1,2,3,4,5,4,3,2,1];

alert(number.indexOf(4));   // 3;
alert(number.lastIndexOf(4)); //5

alert(number.indexOf(4, 4)); //5
alert(number.lastIndexOf(4, 4)); //3

var person = {name: "Nicholas"};
var people = [{name: "Nicholas"}];

var morePeople = [person];

alert(people.indexOf(person));     //-1
alert(morePeople.indexOf(person));     //0

```

**八、迭代方法（都不会修改数组中包含的值）**

5个迭代方法。每个方法都接收两个参数：要在每一项上运行的函数和（可选）运行在该函数的作用域对象---影响this的 值。

传入这些方法中的函数会接收3个参数：数组项的值、该项所在位置、数组对象本身

1、every(): 对数组中的每一项运行给定函数，如果该函数对每一项都返回true,则返回true.

2、some(): 对数组中的每一项运行给定函数，如果该函数对任意一项都返回true,则返回true.

3、filter(): 对数组中的每一项运行给定函数,返回该函数会返回true的项组成的数组.

4、map():  对数组中的每一项运行给定函数,返回每次函数条用的结果组成的数组.

5、forEach(): 对数组中的每一项运行给定函数.这个方法没有返回值。

例：
```
var numbers = [1,2,3,4,5,4,3,2,1];

var everyResult = numbers.every(function(item, index, array){
     return (item>2);
})

alert(everyResult);      //false

var someResult = numbers.some(function(item, index, array){
     return (item>2);
})

alert(someResult);      //true
```

**every()方法要求每一项符合要求则返回true.some()方法要求至少有一项满足要求，则返回true.**

```
var numbers = [1,2,3,4,5,4,3,2,1];

var filterResult = numbers.filter(function(item, index, array){
     return (item>2);
})

alert(filterResult);      //[3,4,5,4,3]

var mapResult = numbers.map(function(item, index, array){
     return item*2;
})

alert(mapResult);      //[2,4,6,8,10,8,6,4,2]
```

**filter()方法返回符合要求的项组成的数组，map()方法返回每一项都是在原始数组中的对应项上运行传入函数的结果。**

```
var numbers = [1,2,3,4,5,4,3,2,1];

var forEachResult = numbers.forEach(function(item, index, array){
     //执行某些操作
});

```

**forEach()方法没有返回值，本质上与使用for循环迭代数组一样。**

**九、归并方法**

reduce()和reduceRight().这两个方法会迭代数组的所有项，然后构建一个最终返回值。其中，reduce()方法从数组第一项开始，逐个遍历到最后.
而reduceRight()则从数组的最后一项开始，向前遍历到第一项。

这两个方法都接收两个参数：一个在每一项上调用的函数和（可选的）作为归并基础的初始值。传给reduce()和reduceRight()的函数接收4个参数：
前一个值、当前值、项的索引、数组对象。

这个函数返回的任何值都会作为第一个参数自动传给下一项。第一次迭代发生在数组的第二项上，因此第一个参数是数组的第一项，第二个参数是数组的第二项。

```
var values = [1,2,3,4,5];

var sum = values.reduce(function(perv, cur, index, array){
  return prev + cur;
});

alert(sum);       //15
```
第一次执行函数，prev是1，cur是2,第二次prev是3，cur是3，这个过程会持续到把数组每一项都访问一遍，最后返回结果。

reduceRight()的作用类似，不过方向相反。

```
var values = [1,2,3,4,5];

var sum = values.reduceRight(function(perv, cur, index, array){
  return prev + cur;
});

alert(sum);       //15
```

第一次执行函数，prev是5，cur是4,第二次prev是9，cur是3.

reduce()还是reduceRight()。主要取决于从哪头开始遍历数组，除此之外毫无差别。







