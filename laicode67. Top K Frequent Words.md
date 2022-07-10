# laicode67. Top K Frequent Words
**Given a composition with different kinds of words, return a list of the top K most frequent words in the composition.**    

Assumptions     

the composition is not null and is not guaranteed to be sorted        
K >= 1 and K could be larger than the number of distinct words in the composition, in this case, just return all the distinct words
Return    

a list of words ordered from most frequent one to least frequent one (the list could be of size K or smaller than K)      

Examples      

Composition = ["a", "a", "b", "b", "b", "b", "c", "c", "c", "d"], top 2 frequent words are [“b”, “c”]     
Composition = ["a", "a", "b", "b", "b", "b", "c", "c", "c", "d"], top 4 frequent words are [“b”, “c”, "a", "d"]       
Composition = ["a", "a", "b", "b", "b", "b", "c", "c", "c", "d"], top 5 frequent words are [“b”, “c”, "a", "d"]     

## Solution
```java
public class Solution {
      public String[] topKFrequent(String[] combo, int k) {
        // Write your solution here
        // Step one: iterate over the composition, and for each word read, count its frequency by
        // -> O(n) time in avergae, O(n^2) time in worst case
        // -> O(# of distinct words) space map
        // Step two: 再Tok K: maintain a MIN heap of size k --> compare by frequency --> top k frequent candidates.
        
        HashMap<String, Integer> freqMap = new HashMap<>();
       
        for(String c : combo){
            Integer ct = freqMap.get(c);
            // 如果map里没有这个元素返回的是null
            if(ct == null){
                freqMap.put(c, 1);
            }else{
                freqMap.put(c, ct + 1);
            }
        }
        
        // 在构造一个PriorityQueue想按照HashMap里的value大小排序时
        // Map.Entry 是 Map 声明的一个内部接口，此接口为泛型，定义为Entry<K, V>. 它表示Map中的一个实体
        // 一个key-value对。接口中有getKey(), getValue()方法。
        
        PriorityQueue<Map.Entry<String, Integer>> minHeap = new PriorityQueue<>(k,
                new Comparator<Map.Entry<String, Integer>>(){
                    @Override
                    public int compare(Map.Entry<String, Integer> e1, Map.Entry<String, Integer> e2){
                        return e1.getValue() - e2.getValue();
                    }
                });

        // HashMap<String, Integer> hashMap = new HashMap<>();
        // hashMap.put("wxy",24);
        // hashMap.put("whp",23);
        // hashMap.put("yjq",24);
        // System.out.println(hashMap.entrySet());  [yjq=24, wxy=24, whp=23]
        // System.out.println(hashMap.keySet());  [yjq, wxy, whp]
        // System.out.println(hashMap.values());  [24, 24, 23]
        
        for (Map.Entry<String, Integer> n : freqMap.entrySet()){
            if(minHeap.size() < k){
                minHeap.offer(n);
            }else if(n.getValue() > minHeap.peek().getValue()){
                minHeap.poll();
                minHeap.offer(n);
            }
        }

        // 从后往前放
        String[] result = new String[minHeap.size()];
        for(int i = minHeap.size() - 1; i >= 0; i--){
            result[i] = minHeap.poll().getKey();
        }

        return result;
    }
}
```
