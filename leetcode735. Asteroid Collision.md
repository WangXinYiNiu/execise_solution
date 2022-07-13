# leetcode735. Asteroid Collision.md
We are given an array asteroids of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.

Example 1:
```
Input: asteroids = [5,10,-5]    
Output: [5,10]      
Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide. 
```

Example 2:
```
Input: asteroids = [8,-8]
Output: []
Explanation: The 8 and -8 collide exploding each other.
```
Example 3:
```
Input: asteroids = [10,2,-5]
Output: [10]
Explanation: The 2 and -5 collide resulting in -5. The 10 and -5 collide resulting in 10.
```

## Solution
```java
class Solution {
    public int[] asteroidCollision(int[] asteroids) {
        // 用top当栈顶
        // 如果和栈顶同符号或者栈顶往右走(>0) i元想向左走(<0)
        int top = 0; // top 就放的是该元素 从i = 1开始看
        for (int i = 1; i < asteroids.length; i++) {
            // 如果不发生碰撞就堆栈
            if (top < 0 || !ifCollision(asteroids, i, top)) {
                asteroids[++top] = asteroids[i];
                // 发生碰撞
            } else {
                // 如果相互碰撞我就栈顶左移动
                int left = Collision(asteroids, i, top);
                // 如果俩个星球相互碰撞了 就栈顶左移动 -> 去下一层查看下一个元素
                if (left == 0) {
                    top--;
                } else {
                    // 发生碰撞
                    // top - 1 其实是栈顶放的那个元素
                    asteroids[top] = left;
                    // 继续碰撞
                    while (top > 0 && ifCollision(asteroids, top, top - 1)) {
                        int collision = Collision(asteroids, top, top - 1);
                        if (collision == 0) {
                            top-=2;
                        }else {
                            asteroids[top - 1] = collision;
                            top--;
                        }
                    }
                }
            }
        }
        return Arrays.copyOf(asteroids, top + 1);
    }

    public boolean ifCollision(int[] asteroids, int i, int j) {
        if (asteroids[i] < 0 && asteroids[j] > 0) {
            return true;
        }
        return false;
    }

    public int Collision(int[] asteroids, int i, int j) {
        if (asteroids[i] + asteroids[j] == 0) {
            return 0;
        }
        if (asteroids[i] < 0 && asteroids[j] > 0) {
            return Math.abs(asteroids[i]) > Math.abs(asteroids[j]) ? asteroids[i] : asteroids[j];
        }
        return 0;
    }
}
```

TC: O(n)    
SC: O(1)    
