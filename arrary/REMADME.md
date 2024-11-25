# 数组

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





