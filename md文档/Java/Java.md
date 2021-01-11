# Java

![https://images0.cnblogs.com/blog/490648/201308/18174126-653273ab5abe491bb9724353360ed252.png](https://images0.cnblogs.com/blog/490648/201308/18174126-653273ab5abe491bb9724353360ed252.png)

<img src="Java8-实战.assets/image-20201114114943110.png" alt="image-20201114114943110" style="zoom:50%;" />

# 随笔

### 键盘读入

```java
import java.util.*;
public class Main{
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        while(sc.hasNext()) {
            int n = sc.nextInt();
            String[] strs = new String[n];
            for(int i = 0; i < n; i++) {
                strs[i] = sc.next();
            }
        }
    }
}

BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
reader.readLine();
```

