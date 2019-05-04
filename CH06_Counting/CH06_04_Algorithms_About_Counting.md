<font size=6>Chaptcer 06 Counting 计数</font>

Part 04 Algorithms About Counting 排列组合算法

covering 6.6 and more

------

> Disclaim: the codes in this section are not tested, it just wants to show you the thoughts behind the algorithms

# Generating Permutations 生成排列

> 给定某一个排列，生成按照字典序升序的下一个排列

先从后往前遍历，直到遇到不是降序的第一个数。然后用该数右边大于该数的数中最小的数替换该数，右边剩下的数（含刚刚换下来的数）升序重排即可。

代码：

```c++
void next_permutation(int* a, int n) // 上一个排列为a，a中有n个数，将a转化为下一个排列
{
    // STEP 1 找到打破降序的第一个数
    int i = n - 2;
    for ( ; i >= 0; i--)
    {
        if (a[i] < a[i + 1])
            break;
    }
    // STEP 2 找到该数右边最大的数
    int k = n - 1;
    for ( ; k > i; k--)
    {
        if (a[k] > a[i])
            break;
    }
    // STEP 3 交换这两个数
    int temp = a[i];
    a[i] = a[k];
    a[k] = temp;
    // STEP 4 右边余下的数升序重排
    sort(a + i, a + n);
}
```

# Find the ordinal number for the given permutation 给定排列求序号

> 基本思想：算出有多少个排列比给定排列小

例如：整数1~k的一个排列$$a_1,a_2,…,a_k$$，求其序号

首先，1到$$a_1-1$$放在第一位，会有$$(a_1-1)\times((k-1)!)$$个排列

其次，1到$$a_2-1$$放在第二位，会有$$(a_2-1)\times((k-2)!)$$个排列

之后，1到$$a_3-1$$放在第三位，会有$$(a_3-1)\times((k-3)!)$$个排列

……

全部加起来，即得到序号

代码：

```c++
int index_of_permutation(int* a, int n)
{
    // 递推算好1~(n-1)的阶乘，做好准备
    int factorial[n];
    factorial[0] = 1;
    for (int i = 1; i < n; i++)
        factorial[i] = factorial[i - 1] * i;
    // 计算答案
    int res = 0;
    for (int i = 0; i < n; i++)
        res += (a[i] - 1) * factorial[n - i - 1];
    return res;
}
```

# Find the permutation given the ordinal number 给定序号求排列

> 基本思想：逐位确定

例如：1234排列的第9号

假设第一位是1，`1___`，能数到$$3!$$个，没有达到9，故第一位至少为2

假设第一位是2，`2___`，能数到$$2\times 3!$$个，到达了9，故第二位为2

假设第二位是1，`21__`，能数到$$3!+2!=8$$个，没达到9，故第二位至少为3

假设第二位为3，`23__`，能数到$$3!+2\times 2!=10$$个，达到了9，故第二位为3

假设第三位为1，`2314`，能数到$$3!+2!+1=9$$个，因此找到所需数为2314

代码：

```c++
int* permutation_from_index(int index, int n)
{
    // 递推算好1~n的阶乘，做好准备
    int factorial[n + 1];
    factorial[0] = 1;
    for (int i = 1; i <= n; i++)
        factorial[i] = factorial[i - 1] * i;
    // 构建答案
    int *res = new int[n];
    bool used[n + 1];
    memset(used, 0, sizeof(used));
    for (int i = 0; i < n; i++) // 尝试第i位
    {
        for (int j = 1; j <= n; j++) // 尝试1~n
        {
            if (!used[j])
                if (factorial[n - i - 1] >= index + 1)
                    break;
            	else
                    index -= factorial[n - i - 1];
        }
        res[i] = j;
        used[j] = true;
    }
    return res;
}
```

# Generating Combinations 生成组合

## 位串表示下的生成组合

计算机中可以使用位串来表示组合，因此我们只需生成下一个位串即可

这就等价于二进制下加1

当然`int`范围内的我们可以直接加1，但是考虑更加一般化的情景，比如储存在数组或者链表中的位串

代码如下：

```c++
void next_bit_string(int* b, int n)
{
    for (int i = n - 1; i >= 0; i--)
    {
        if (b[i] == 1)
            b[i] = 0;
        else
        {
            b[i] = 1;
            break;
        }
    }
}
```

## 常规数字数组下的生成组合

如果单纯是用数组存放的组合，也是可以生成排列的，算法如下（规定每个有效的数组中元素都是升序排列的）：

```c++
void next_r_combination(int* a, int n, int r)
{
    for (int i = r - 1; i > 0; i--)
    {
        if (a[i] != n - r + 1 + i)
        {
            a[i]++;
            for (int j = i + 1; i < r; i++)
                a[j] = a[i] + j - i;
            break;
        }
    }
}
```

