# ;数组

## 创建

### ```const arr = [];```

### ```new Array(2)```

## 访问和遍历

### file()进行填充

### for循环

### forEach()

### map()



无特殊需求建议使用for循环遍历，性能最快。



## 二维数组



**二维数组就是矩阵**



### 初始化二维数组

```
const len = arr.length
for(let i=0;i<len;i++) {
    // 将数组的每一个坑位初始化为数组
    arr[i] = []
}

```

### 访问二维数组

```
// 缓存外部数组的长度
const outerLen = arr.length
for(let i=0;i<outerLen;i++) {
    // 缓存内部数组的长度
    const innerLen = arr[i].length
    for(let j=0;j<innerLen;j++) {
        // 输出数组的值，输出数组的索引
        console.log(arr[i][j],i,j)
    }
}

```



##　栈和队列

在 JavaScript 中，**栈和队列的实现一般都要依赖于数组**，大家完全可以把栈和队列都看作是“特别的数组。

### 灵活增删的数组

#### 数组中增加元素的三种方法

- unshift()添加到头部
- push()添加到尾部
- splice()添加元素到数组任何位置

```
const arr = [1,2]
arr.unshift(0) // [0,1,2]
arr.push(3) // [0,1,2,3]
arr.splice(1,0,3) // [0,1,3,2,3]
```



#### 数组中删除元素的三种方法

- shift()删除头部的元素
- pop()删除尾部的元素
- splice()删除任意位置的元素

```;
const arr = [1,2,3]
arr.shift() // [2,3]
arr.pop() // [2]
arr.push(3); //[2,3]
arr.splice(0,1); //[3]
console.log(arr);
```



### 栈（Stack）——只用 pop 和 push 完成增删的“数组”

栈是“后进先出”，只允许从尾部添加元素和尾部取出元素

```
let car = [
    'benz',
    'audi',
    'xp'
];
car.push('bmw');
car.push('changcheng');
car.pop();
console.log(car);

while(car.length>0) {
    const top = car.pop();
    console.log('取出的车是',top);
}
console.log(car); // [] 空栈
```

### 队列（Queue）——只用 push 和 shift 完成增删的“数组”

队列的特点是先进先出，即只允许从尾部加入元素，从头部取出元素。

```
let kfcQueue = [];
kfcQueue.push('小李');
kfcQueue.push('小王');
kfcQueue.push('小孙');
kfcQueue.push('tom');

while (kfcQueue.length > 0) {
    let getKfc = kfcQueue[0];
    kfcQueue.splice(0, 1);
    console.log('此时取餐的是', getKfc);
}
console.log(kfcQueue); // []
```

### 链表

链表和数组相似，它们都是有序的列表、都是线性结构（有且仅有一个前驱、有且仅有一个后继）。不同点在于，链表中，数据单位的名称叫做“结点”，而结点和结点的分布，在内存中可以是**离散**的。



在链表中，每一个结点的结构都包括了两部分的内容：数据域和指针域。JS 中的链表，是以嵌套的对象的形式来实现的

```
{
	val:'1-1',
	next:{
		val:'1-1-1',
		next:...
	}
}
```

创建一个节点，并制定其的下一个节点

```
function ListNode(val){
    this.val = val;
    this.next = null;
}
let header = new ListNode('header');
header.next = new ListNode(1);
```

#### 链表增加节点

要考虑添加位置的前置节点，把前置节点的next修改为添加的节点，添加的节点的后置节点修改为添加位置的下一个节点

```
function ListNode(val){
    this.val = val;
    this.next = null;
}
let header = new ListNode('header');
let node = new ListNode(1);
header.next = node;

let midNode = new ListNode('mid');
header.next = midNode;
midNode.next = node;

```



#### 链表删除节点

```
function ListNode(val){
    this.val = val;
    this.next = null;
}
let header = new ListNode('header');
let node = new ListNode(1);
header.next = node;

let midNode = new ListNode('mid');
header.next = midNode;
midNode.next = node;


// 删除第一个节点，起始位置为第0个节点
header.next = header.next.next;
// 将被删除的节点断链
midNode.next = null;
```



### 数组和链表的区别



如果数组中只定义了一种类型，那么就是这就是“真正的数组”，即对应了一段连续的内存空间

```
const arr = [1,2,3,4];
```



如果定义了不同类型的元素，那么其对应的就是一段非连续的内存，此时，JS 数组不再具有数组的特征，其底层使用哈希映射分配内存空间，是由对象链表来实现的。

```
const arr = [1,'a',{val:'3'}];
```



#### 性能

数组的增删改的操作复杂度是O(n)，n为数组长度

链表的增删改的操作复杂度时O(1)

数组的访问操作复杂度是O(1),

链表的访问复杂度是O(n),n搜索长度



**链表的插入/删除效率较高，而访问效率较低；数组的访问效率较高，而插入效率较低。**
