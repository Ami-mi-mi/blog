##һ���������
###1��instanceof
```
if(value instanceof Array) {
//���������ĳЩ����
}
```

###2��isArray
```
if(Array.isArray(value)) {
//���������ĳЩ����
}
```

##����ת������

���ж��󶼾���toLocaleString()��toString()��valueOf()������

1������toString()�����᷵����������ÿ��ֵ���ַ�����ʽƴ�Ӷ��ɵ�һ���Զ��ŷָ����ַ�����

2������valueOf()���صĻ������顣

3������toLocaleString()�����᷵����������ÿ��ֵ���ַ�����ʽƴ�Ӷ��ɵ�һ���Զ��ŷָ����ַ�����

ʵ���ϣ�Ϊ�˴�������ַ������������ÿһ���toString()������
```
var colors = ["red", "blue", "green"]; //����һ������3���ַ���������
alert(colors.toString()); //colors,blue,green
alert(colors.valueOf()); //colors,blue,green
alert(colors); //colors,blue,green
```
��һ��alert���������Ƿ����Զ��ŷָ����ַ������ڶ��͵����������������ľ������Ҳ���ص����Զ��ŷָ����ַ�����ԭ������alertҪ�����ַ������������������ٺ�̨����toString������valueOf()���Ƿ�������ġ�

##����ջ������LIFO  Last-in-First-Out ����ȳ���

1��push ����ĩβ���룬�����޸ĺ�����ĳ���

2��pop ����ĩβɾ�������ص�ǰɾ������

##�ġ����з���(FIFO First-in-First-Out �Ƚ��ȳ�)

1��push ����ĩβ���룬�����޸ĺ�����ĳ���

2��shift ɾ�������һ����ص�ǰɾ������


unshift �������ǰ�˼������������ĳ��ȡ���pop���ʹ�ÿ��Դ��෴����ģ����У���������ǰ�˼��������ĩβ�Ƴ��

##�塢�����򷽷�
###1��reverse������ת�������˳��
```
var values = [1,2,3,4];
values.reverse();
alert(values);         //5,4,3,2,1
```

###2��sort()
Ĭ���������������������---����С��λ����ǰ�棬����λ������档
Ϊ��ʵ������sort()�������������ÿһ���toString()ת�ͷ�����Ȼ��Ƚϵõ����ַ�������ȷ���������
��ʹ�����е�ÿһ�����ֵ��sort()�����Ƚϵ�Ҳ���ַ�����

```
var values = [0,1,5,10,15];
values.sort();
alert(values);                 //0,1,10,15,5
```

sort()��������һ���ȽϺ�����Ϊ�������ȽϺ���������������

```
function compare(v1,v2){
     if(v1 < v2){                 //����
       return -1;
     }else if(v1 > v2) {          //����
       return 1;
     }else {
       return 0;
     }
}

��

function compare(v1, v2) {
    return v2-v1;
}
```

##������������
###1��concat()   
����������ȴ���һ������ĸ�����Ȼ�󽫽��յ��Ĳ�����ӵ����������ĩβ����󷵻��µ����顣
��û�и��÷������ݲ������������ֻ�Ǹ��Ƶ�ǰ���鲢���ظ�����������ݴ�concat() ��������һ�������飬��÷����Ὣ��Щ�����е�ÿһ���ӵ���������С�
������ݵ�ֵ�������飬��Щֵ�ᱻ�򵥵���ӵ���������ĩβ��

```
var colors = ["red", "green", "blue"];
var colors2 = colors.concat("yellow", ["black", "brown"]);

alert(colors);           //red,green,blue
alert(colors2);          //red,green,blue,yellow,black,brown

```
###2��slice() ������Ӱ��ԭʼ���飩
���ܹ����ڵ�ǰ�����е�һ�������һ���µ����顣
slice()����һ��������������Ҫ���������ʼ�ͽ���λ�á�
��ֻ��һ������������£�slice()�������شӸò���ָ����λ�õ���ǰ����ĩβ�������
����������������÷���������ʼ�ͽ���λ��֮�����---���ǲ���������λ�õ��

```
var colors = ["red", "green", "blue", "yellow", "purple"];
var colors2 = colors.slice(1);
var colors3 = colors.slice(1,4);

alert(colors2);           //green,blue,yellow,purple
alert(colors3);           //green,blue,yellow

```

_���slice()������������һ���������������鳤�ȼ��ϸ�����ȷ����Ӧ��λ�á��������λ��С������λ���򷵻ؿ����顣_

###3��splice() (��ı�ԭʼ����)
��Ҫ��;���������в����

1��**ɾ��**������ɾ�������������ֻ��ָ��2��������Ҫɾ���ĵ�һ��λ�ú�Ҫɾ����������
���磺 splice(0,2) ��ɾ�������е�ǰ���

2��**����**��������ָ��λ�ò��������������ֻ���ṩ3����������ʼλ�ã�0��ɾ��0�����������������������ڴ�����ĵ��������������
���磺`splice(2, 0, "red", "green")` ��ӵ�ǰ�����λ��2��ʼ�����ַ��� red �� green��

3��**�滻**��������ָ��λ�ò����������ͬʱɾ�������������ֻ��ָ��3����������ʼλ�ã�ɾ����������������1����������������ɾ�������ȡ�
���磺 `splice(2, 1, "red", "green")`���λ��2��ʼɾ��1��ٴ�λ��2��ʼ�����ַ��� red �� green.

```
var colors = ["red", "green", "blue"];
var removed = colors.splice(0,1);               //ɾ����һ��
alert(colors);                                  //red,green,blue
alert(removed);                                  //red

removed = colors.splice(1, 0, "yellow", "orange"); //��λ��1��ʼ���� yellow �� orange
alert(colors);                                     //green,yellow,orange,blue
alert(removed);                                      //���ؿ�����

removed = colors.splice(1, 1, "red", "purple");   //��λ��1��ʼɾ��һ���ͬʱ����2��
alert(colors);                                    //green,red,purple,orange,blue
alert(removed);                                    //yellow       ����ɾ������

```

_splice()����ʼ�շ���һ�����飬���������������ɾ����������û��ɾ���κ���򷵻ؿ����飩_

##�ߡ�λ�÷��� 
indexOf()��lastndexOf(),��������������������������Ҫ���ҵ���ͣ���ѡ����ʾ����λ������������

1��indexOf()���������鿪ͷ��λ��Ϊ0����ʼ�����ҡ�
2��lastIndexOf()������������ĩβ��ʼ��ǰ���ҡ�

����������������Ҫ���ҵ����������е�λ�ã�������û�ҵ�������·���-1.�ٱȽϵ�һ�������������е�ÿһ��ʱ����ʹ��ȫ�Ȳ�������Ҳ����Ҫ����ҵ�������ϸ���ȣ�����ʹ�� ===һ����

���磺
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

##�ˡ������������������޸������а�����ֵ��
5������������ÿ����������������������Ҫ��ÿһ�������еĺ����ͣ���ѡ�������ڸú��������������---Ӱ��this�� ֵ��

������Щ�����еĺ��������3���������������ֵ����������λ�á����������

1��every(): �������е�ÿһ�����и�������������ú�����ÿһ�����true,�򷵻�true.
2��some(): �������е�ÿһ�����и�������������ú���������һ�����true,�򷵻�true.
3��filter(): �������е�ÿһ�����и�������,���ظú����᷵��true������ɵ�����.
4��map():  �������е�ÿһ�����и�������,����ÿ�κ������õĽ����ɵ�����.
5��forEach(): �������е�ÿһ�����и�������.�������û�з���ֵ��

����
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

**every()����Ҫ��ÿһ�����Ҫ���򷵻�true.some()����Ҫ��������һ������Ҫ���򷵻�true.**

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

**filter()�������ط���Ҫ�������ɵ����飬map()��������ÿһ�����ԭʼ�����еĶ�Ӧ�������д��뺯���Ľ����**

```
var numbers = [1,2,3,4,5,4,3,2,1];

var forEachResult = numbers.forEach(function(item, index, array){
     //ִ��ĳЩ����
});

```

**forEach()����û�з���ֵ����������ʹ��forѭ����������һ����**

##�š��鲢����

reduce()��reduceRight().�������������������������Ȼ�󹹽�һ�����շ���ֵ�����У�reduce()�����������һ�ʼ��������������.
��reduceRight()�����������һ�ʼ����ǰ��������һ�

��������������������������һ����ÿһ���ϵ��õĺ����ͣ���ѡ�ģ���Ϊ�鲢�����ĳ�ʼֵ������reduce()��reduceRight()�ĺ�������4��������
ǰһ��ֵ����ǰֵ������������������

����������ص��κ�ֵ������Ϊ��һ�������Զ�������һ���һ�ε�������������ĵڶ����ϣ���˵�һ������������ĵ�һ��ڶ�������������ĵڶ��

```
var values = [1,2,3,4,5];

var sum = values.reduce(function(perv, cur, index, array){
  return prev + cur;
});

alert(sum);       //15
```
��һ��ִ�к�����prev��1��cur��2,�ڶ���prev��3��cur��3��������̻������������ÿһ�����һ�飬��󷵻ؽ����

reduceRight()���������ƣ����������෴��

```
var values = [1,2,3,4,5];

var sum = values.reduceRight(function(perv, cur, index, array){
  return prev + cur;
});

alert(sum);       //15
```

��һ��ִ�к�����prev��5��cur��4,�ڶ���prev��9��cur��3.

reduce()����reduceRight()����Ҫȡ���ڴ���ͷ��ʼ�������飬����֮����޲��







