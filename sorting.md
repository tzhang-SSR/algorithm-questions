# 排序算法
## 冒泡排序

冒泡排序会遍历数组，对比相邻的两个元素，如果前一个元素大于后一个元素，则交换两个元素的位置，

这样一次遍历之后，最大的元素就会被交换到数组的最后面，然后再次遍历数组，重复上述操作，直到数组完全有序。

### 时间复杂度
- 最好情况：O(n)
- 最坏情况：O(n^2)

### 空间复杂度
- O(1)

```js
const bubbleSort = (arr) => {
    for(let i = 0; i < arr.length; i++){
        let isSorted = true
        for(let j = 0; j < arr.length - i; j++){
            if(arr[j] > arr[j+1]){
                isSorted = false
                let temp = arr[j + 1]
                arr[j + 1] = arr[j]
                arr[j] = temp
            }
        }
        if(isSorted){
            return
        }
    }
}
```

## 选择排序

选择排序遍历数组，找到最小的元素，将其放到数组的最前面，然后再从剩下的元素中找到最小的元素，放到数组的第二个位置，以此类推，直到数组完全有序。

### 时间复杂度
- 最好情况：O(n^2)
- 最坏情况：O(n^2)
  
### 空间复杂度
- O(1)
  
```js
const selectionSort = (arr) => {
    for(let i = 0 ; i < arr.length - 1; i++){
        let minIndex = i
        for(let j = i + 1; j < arr.length; j++){
            if(arr[j] < arr[minIndex]){
                minIndex = j
            }
        }
        let temp = arr[i]
        arr[i] = arr[minIndex]
        arr[minIndex] = temp
    }
}
```
## 插入排序
插入排序把数组分为两部分：
- 一部分是已经排序的
- 一部分是未排序的，

### 时间复杂度
- 最好情况：O(n)
- 最坏情况：O(n^2)

### 空间复杂度
- O(1)

遍历未排序的部分，将元素插入到已经排序的部分，直到数组完全有序。
```js
const insertionSort = (arr) => {
    for(let i = 1; i < arr.length; i++){
        let preIndex = i - 1
        let current = arr[i]
        while(preIndex >= 0 && arr[preIndex] > current){
            arr[preIndex+1] = arr[preIndex]
            preIndex--
        }
        arr[preIndex+1]=current
    }
}
```

## 快速排序
快速排序的核心是分治法（divide and conqueor）和递归，将数组分为两部分，一部分是小于基准值的，一部分是大于基准值的，然后再对这两部分进行快速排序，直到数组完全有序。

基准值的选择有很多，一般选择中间的元素，也可以选择第一个元素或者最后一个元素。

### 时间复杂度
- 最好情况：O(nlogn)
- 最坏情况：O(n^2)

最坏情况是每次选择的基准值都是最大或者最小的元素，这样每次只能将数组分为一个元素和剩下的元素，子数组只会比之前的数组少一个元素， 这样就需要n次递归，所以时间复杂度为O(n^2)。

### 空间复杂度
- O(logn)

```js
function quicksort(array) {
 if(array.length <= 1){
     return array
 }
 const pivot = array[Math.floor(array.length/2)]
 let less = []
 let greater = []
 
 for(let i = 0; i < array.length; i++){
     if(array[i] < pivot){
         less.push(array[i])
     }else if(array[i] > pivot){
         greater.push(array[i])
     }
 }
 
 return [...quicksort(less), pivot, ...quicksort(greater)]
}

```

## 归并排序
归并排序的核心是分治法（divide and conqueor）和递归，
- 将数组分为两部分
- 然后再对这两部分进行归并排序，直到两个数组完全有序。
- 然后再将两个有序的数组合并为一个有序的数组。

### 时间复杂度
- 最好情况：O(nlogn)
- 最坏情况：O(nlogn)
  
### 空间复杂度
- O(n)

```js
function mergeSort(arr) {
    var len = arr.length;
    if(len < 2) {
        return arr;
    }
    const mid = Math.floor(arr.length / 2)
    let left = arr.slice(0, mid)
    let right = arr.slice(mid)
    return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right){
   let result = []
   if(left.length === 0 || right.length === 0){
       return [...left, ...right]
   }
   while(left.length && right.length){
       if(left[0] < right[0]){
           result.push(left.shift())
       }else{
           result.push(right.shift())
       }
   }
   while(left.length){
        result.push(left.shift())
    }
   
    while(right.length){
        result.push(right.shift())
    }
   return result
}
```




## Ref
- https://www.runoob.com/w3cnote/ten-sorting-algorithm.html