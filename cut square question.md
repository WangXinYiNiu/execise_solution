小明有一些矩形材料，他要从这些矩形材料中切割出一些正方形。
当他面对一块矩形材料时，他总是从中间隔一刀，切出一块最大的正方形，剩下一块矩形，然后再切割剩下的矩形材料，知道全部切为正方形为止。
例如，对于一块俩边分别为 5 和 3 的材料（记为 5 * 3），小明会依次切出 3 * 3、 2 * 2、 1 * 1、 1 * 1 共四个正方形。
现在小明有一块矩形的材料，俩边长分别是 2019 和 324。请问小明最终会切出多少个正方形？

```java
public class test09 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int length = scan.nextInt();
        int width = scan.nextInt();
        if(length == width){
            System.out.println(length);
        }
        int res = 0;
        while(length != 0 && width != 0){
            if(length > width){
                length = length - width;
            }else {
                width = width - length;
            }
            res++;
        }
        System.out.println(res);
    }
}
```
tips：画图。取最大的。
