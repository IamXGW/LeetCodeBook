# LeetCodeBook
刷 LeetCode 过程中，总结的一些知识点

#### 迭代器遍历二维数组、两点间距离

```Java
public int numberOfBoomerangs(int[][] points) {
    for (int[] p : points) {
        for (int[] q : points) {
            
            // 这里求距离，如果不是一定需要准确的距离值，可以不用 sqrt，dis 只是一种距离的形式
            int dis = (p[0] - q[0]) * (p[0] - q[0]) + (p[1] - q[1]) * (p[1] - q[1]);
            // double dis = Math.sqrt((p[0] - q[0]) * (p[0] - q[0]) + (p[1] - q[1]) * (p[1] - q[1]));
        }
    }
    // ...
}
```

#### 使用迭代器遍历 Map

```Java
Map<Integer, Integer> record = new HashMap<>();

for (Map.Entry<Integer, Integer> entry : record.entrySet()) {
    int key = entry.getValue();
    int val = entry.getValue();

    // ...
}
```

#### 遍历 Stack 堆栈

```Java
Stack<String> stack = new Stack<>();

for (String s : stack) {
    // ...
}
```

#### floor 和 ceil

```Java
Math.ceil(125.9)=126.0 // 尽可能向坐标轴**右边**靠
Math.ceil(-0.65)=-0.0

Math.floor(125.9)=125.0
Math.floor(-0.65)=-1.0 // 尽可能向坐标轴**左边**靠
```

#### Java 操作字符串

```Java
// 分割字符串
str.split("/");

// 字符串是否包含子自字符串
if (" ..".contains("..")) {
    " "/" ."/" .."/"."/".."
}

// 连接字符串，比如 IP 地址
List<String> res = new ArrayList<>();
List<String> path = new ArrayList<>();

path.add("1");path.add("1");path.add("1");path.add("1");

res.add(String.join(".", path)); 

// 输出：1.1.1.1
```

#### Java 的优先队列 PriorityQueue 默认是最小堆实现，如果改为最大堆

```Java
// 修改为最大堆实现
PriorityQueue<Integer> pq = new PriorityQueue<Integer>(new Comparator<Integer>() {
    @Override
		public int compare(Integer num1, Integer num2) {
        return num2 - num1;
    }
});
```

#### Java 比较器

```Java
PriorityQueue<int[]> queue = new PriorityQueue<int[]>(new Comparator<int[]>() {
    public int compare(int[] m, int[] n) {
        return m[1] - n[1];
    }
});

List<Integer> list = new ArrayList<>();
Collections.sort(list, (a, b) -> (a - b));

Integer[] arrs = new Integer[]{1,4,5,2,3,2};
Arrays.sort(arrs, (a,b) -> (a - b));
Arrays.sort(arrs, (a,b) -> (Math.abs(a) - Math.abs(b)));
Arrays.sort(arrs, (a,b) -> (Integer.compare(Math.abs(a),  Math.abs(b))));
```

#### 取数组中的最大值

```Java
Arrays.stream(dp).max().getAsInt();
```

#### 将 int 转成 char *

```Java
curarr = Character.forDigit((curarr - '0' + 1) % 10, 10);// 10 表示 十进制
```
#### List 常用操作

```Java
// ********** 将多个 list.add() 合为一句话 **********
// List<Integer> subAns = new ArrayList<>();      
// subAns.add(nums[i]);
// subAns.add(nums[left]);
// subAns.add(nums[right]);

// 合为一句话
subAns.add(new ArrayList<>(Arrays.asList(nums[i], nums[left], nums[right])));

// ********** 将 list 转为一个二维数组 **********
List<int[]> list = new ArrayList<>();
return list.toArray(new int[list.size()][]);

// 没有将 List<Integer> list = new ArrayList<>(); 转为 int[] 的方法
// 可以这样：
int[] arr = new int[len]; // len 取合适的长度，根据题意决定
Arrays.copyOfRange(arr, 0, index); // [0, index) 是需要的部分
```

#### 取随机数

```Java
(int) (Math.random() * (r - l + 1)) + l; // Math.random() => [0.0, 1.0)
```

#### 将字母转换大小写

```Java
char c = Character.toLowerCase(s.charAt(0));
Character.toUpperCase();
```

#### 向上取整

```Java
(num + divisor - 1) / divisor
```

#### 拷贝数组

```Java
int n = nums1.length;
int[] rec = new int[n];
System.arraycopy(nums1, 0, rec, 0, n);
```

#### 使用 Set 保证 int[] 数组的唯一性

```Java
// 直接往 Set 里面放 int[] 是不能保证唯一性的。
// 因为 int[] 并没有重写 hashCode 和 equals 方法。
// 因此，
set.add(new int[]{1,2}); 
set.add(new int[]{1,2});
// 打印一下 set 的大小为 2。

// 可以使用 List 来代替 int[]。
l1.add(1);l1.add(2); // 相当于 new int[]{1,2}
set.add(l1);
l2.add(1);l2.add(2); // 相当于 new int[]{1,2}
set.add(l2);
// 打印一下 set 的大小为 1。

// 注意，这里的 list 是有顺序性的。
l1.add(1);l1.add(2); // 相当于 new int[]{1,2}
set.add(l1);
l2.add(2);l2.add(1); // 相当于 new int[]{2,1}
set.add(l2);
// 打印一下 set 的大小为 2。
```

#### 位运算技巧

```Java
// ********** 2 的 n 次幂 **********
int n = 2;
(1 << n) == (Math.pow(2, n)) 
```

#### 快速幂

目的是：

```Java
long fastPow(int x, int n){
    long res = 1;

    while (n > 0){
        if ((n & 1) == 1) res = (res * x);

        n >>= 1;
        x = (x * x);
    }

    return res;
}
```

#### 快速乘

目的是：

```Java
long fastMul(long a, long k) {
    long res = 0;

    while (k > 0) {
        if ((k & 1) == 1) res += a;

        k >>= 1;
        a += a;
    }

    return res;
}
```
