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

## Ref
- https://www.runoob.com/w3cnote/ten-sorting-algorithm.html