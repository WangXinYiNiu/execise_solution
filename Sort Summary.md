1. 为什么quickSort比mergeSort好？   
MergeSort and quickSort both use ```divide and conquer```, and the Code use ```recursion``` to achieve. The process is very similar.  
MergeSort is pretty stable, the time complexity always is ```O(NlogN)```, but it uses extra ```O(n)``` space complexity. It's not an in-place sorting algorithm.
QuickSork is not a stable algorithm. The worst time complexity is ```O(N^2)```, the average is ```O(NlogN)```. But the probability of when the worst situation occurs is very low. The point is quickSort is ```in-place``` sorting algorithm, don't use extra space.  
So, quickSort is more widely used.
