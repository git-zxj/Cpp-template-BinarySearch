# -
来源：https://www.acwing.com/blog/content/31/

# 二分模板一共有两个，分别适用于不同情况。
## 算法思路：假设目标值在闭区间[l, r]中， 每次将区间长度缩小一半，当l = r时，我们就找到了目标值。

版本1
当我们将区间`[l, r]`划分成`[l, mid]`和`[mid + 1, r]`时，其更新操作是`r = mid`或者`l = mid + 1;`，计算mid时不需要加1。

C++ 代码模板：
```c++
int bsearch_1(int l, int r)
{
    while (l < r)
    {
        int mid = l + r >> 1;
        if (check(mid)) r = mid;
        else l = mid + 1;
    }
    return l;
}
```
版本2
当我们将区间`[l, r]`划分成`[l, mid - 1]`和`[mid, r]`时，其更新操作是`r = mid - 1`或者`l = mid;`，此时为了防止死循环，计算mid时需要加1。

C++ 代码模板：
```c++
int bsearch_2(int l, int r)
{
    while (l < r)
    {
        int mid = l + r + 1 >> 1;
        if (check(mid)) l = mid;
        else r = mid - 1;
    }
    return l;
}
```

_作者：yxc
链接：https://www.acwing.com/blog/content/31/
来源：AcWing
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。_
