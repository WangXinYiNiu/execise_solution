# leetcode56. Merge Intervals
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.               
  
Example 1:
```
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]     
Output: [[1,6],[8,10],[15,18]]      
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].       
```

Example 2:    
```
Input: intervals = [[1,4],[4,5]]    
Output: [[1,5]]     
Explanation: Intervals [1,4] and [4,5] are considered overlapping.      
```

Constraints:
```
1 <= intervals.length <= 104      
intervals[i].length == 2      
0 <= starti <= endi <= 104      
```

所谓区间问题，就是线段问题，让你合并所有线段、找出线段的交集等等。主要有两个技巧：

1、排序。常见的排序方法就是按照区间起点排序，或者先按照起点升序排序，若起点相同，则按照终点降序排序。当然，如果你非要按照终点排序，无非对称操作，本质都是一样的。               
2、画图。就是说不要偷懒，勤动手，两个区间的相对位置到底有几种可能，不同的相对位置我们的代码应该怎么去处理。          

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        if(intervals.length <= 1){
            return intervals;
        }
        Arrays.sort(intervals, new Comparator<int[]>(){
            public int compare(int[] i1, int[] i2){
                return i1[0] - i2[0];
            }
        });
        int prevStart = intervals[0][0];
        int prevEnd = intervals[0][1];
        List<int[]> result = new ArrayList<>();
        for(int i = 1; i < intervals.length; i++){
            int curStart = intervals[i][0];
            int curEnd = intervals[i][1];
            if(curStart <= prevEnd){
                prevEnd = Math.max(prevEnd, curEnd);
            }else{
                result.add(new int[] {prevStart, prevEnd});
                prevStart = curStart;
                prevEnd = curEnd;
            }
        }
        result.add(new int[] {prevStart, prevEnd});
        int[][] matrix = new int[result.size()][];
        for(int i = 0; i < matrix.length; i++){
            matrix[i] = result.get(i);
        }
        return matrix;
    }
}
```

