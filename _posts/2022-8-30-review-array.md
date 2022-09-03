---
layout: post
title: Flake it till you make it
subtitle: Excerpt from Soulshaping by Jeff Brown
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [books, test]
---
​​
# Java基础
## 数组的使用

### 动态初始化之一

~~~java

//a.length = 5

int[] a = new int[5];

~~~

标记：

+ 不同于<b>int a = 5;</b>这种语句,前者数组名a代表着一个地址，后者变量名a代表着一个数字5

+ 上面int[5]是开辟了一个大块的空间，大块空间中是5块连续的小块，它们的地址也是连续的

+ 开辟出来的空间如果未在这块地址中赋值，那么默认为该数据类型的默认值

### 动态初始化之二

~~~java

//a.length=???

int[] a;

//......

//calculate b+c=d

//b=???,c=???,d=???

int b = new Scanner(System.in).nextInt();

int c = new Scanner(System.in).nextInt();

int d = b + c;

//a.length = d;

a = new int[d];

~~~

标记：

+ 先声明a是一个数组，不指向堆中任何一块空间

+ 知道了具体要开辟多大内存空间后，再初始化数组对象，使a指向初始化的对象

### 静态初始化

~~~java

int[] a = {1,2,3,4,5,6};

~~~

标记：

+ 连续的六块地址中都从一开始被填入了元素

+ 适用于你把数组中的数字全都确定了

## 数组使用注意事项和细节

1. 数组只能存相同的数据类型，无论是引用数据类型还是基本数据类型

2. 开辟出的每一块地址中，如果没有放入数值，就是类型默认数值

3. 数组名指向一个对象，基本数据类型变量名等于一个数字/字符/字符串

## 数组赋值机制

数组在默认情况下是引用传递，赋的值是地址

~~~java

//arr1 = &arr1[0]

int[] arr1 = {1,2,3};

//arr2 = arr1 = &arr1[0]

int [] arr2 = arr1;

~~~

标记：

+ 上面这波操作是让arr2也指向arr1指向的那片地址，操作arr2指向的地址里的东西也就等价于arr1指向的地址里的东西

图解:
![在这里插入图片描述](https://img-blog.csdnimg.cn/1f9ffd12999c4982b2a4f106668ad2a8.png#pic_center)
## 数组拷贝
~~~java
int[] array2 = new int[array1.length];
for(int i = 0;i<array1.length;i++){
	array2[i] = array1[i];
}
~~~
标记：
+ 这样的话修改array2的值不会影响到array1，因为array2是一块新的空间

## 数组翻转
### 1.通过双指针翻转
~~~java
int[] a = {1,2,3,4,5,6};
//头指针
int head = 0;
//尾指针
int tail = a.length-1;
//开始遍历
while(true){
	if(tail<=head){
		break;
	}
	a[head] = a[head]^a[tail];
	a[tail] = a[head]^a[tail];
	a[head] = a[head]^a[tail];
	tail--;
	head++;
}
~~~
### 2.新数组逆序赋值
这个个人感觉不用再写了，就略过了。

## 数组扩容
新建一个比原来数组容量大n个空间的数组，然后把原来的数组每个值赋值进去，再最后写上你要添加的数组，再使原来的数组指向新数组的地址
## 数组缩减
思路同上，就是地址的来回指

## 冒泡排序
...这真不是我眼高手低，这真的略了

## 二分查找(已经排好序)
~~~java
//目标值
int goal = 100;
//定义初始指针位置
int index = array.length/2;
//整个的范围
int left = 0;
int right = array.length;
//开始查找
while(true){
	if(array[index]==goal){
		break;
	}
	else if(array[index]>goal){
		left = index;
		index = (left+right)/2;
	}
	else{
		right = index;
		index = (left+right)/2;
	}
}
~~~
## 二维数组内存布局
~~~java
int[][] a = new int[3][2];
~~~
标记：
+ a在栈中的值为一个地址，这个地址指向堆中的一个大空间，堆中有3个连续空间，这两个空间中所存都是地址，这3个地址分别又指向堆中的一个新空间（2个小空间）

图解:
![](https://img-blog.csdnimg.cn/2019032612285365.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwODE3ODI3,size_16,color_FFFFFF,t_70)<b>图片引用自围巢111</b>

## 二维数组使用
### 动态初始化之一
~~~java
int[][] a = new int[3][2]
~~~
标记：
+ a的值是一个地址，这个地址指向堆中的一个空间，这个空间中连续的存着三个地址，三个地址又指向另外的空间

### 动态初始化之二
~~~java
int[][] a;
a = new int[3][2];
~~~
### 动态初始化之单独开辟一维数组
~~~java
int[][] a = new int[3][];
for(int i = 0;i<a.length;i++){
	a[i] = new int[i+1];
}
~~~
标记：
+ Line1中我们只开辟了3个存放地址的空间，而未在这个空间中放任何地址，所以此时等价于一维数组，默认值为0
+ for循环中，我们给3个空间中的每一个空间都赋上一个地址值，这样就变成了三个长度不用的一维数组所组成的二维数组

### 静态初始化
~~~java
int[][] a ={1,2},{3},{5,9,0,7};
~~~
标记：
+ a中有三个一维数组（三块空间存地址），第一个指向一维数组有两个元素，第二个指向一维数组有一个元素，第三个指向一维数组有四个元素
