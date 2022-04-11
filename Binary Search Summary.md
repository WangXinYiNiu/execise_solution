# Binary Search Summary

二分法
条件 : 必须要是sorted

## Process:
 step 1: 每次取中间
 取中间一分为二 - mid = left + (right - left) / 2;    
 mid = (right + left) / 2 ,这种写法存在问题: Integer有上下限 -- left 和 right 可以保证在范围内，但是left + right 就无法保证了。   
 但是计算机位运算比除法快，故可以改成 left + ((right - left) >> 1) (ps:为运算的优先级比较低于加减乘除，所以要带上括号)

 step 2: target 和 array[mid] 比较，去该去的一半

 step 3: 缩小范围 -- 确定新的 left 和 right 边界
    只要确保有一丝可能要的元素能够在新的范围内找到即可， 没有可能出现的坚决不要

注意 : 循环条件 -- 来控制最后出循环有几个数
       while (left < right) -- 这样写的话， 当left 比 right 小1的时候，mid会一直等于left，导致死循环
