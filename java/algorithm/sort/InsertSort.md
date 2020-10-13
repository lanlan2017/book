# 1.2 插入排序

## 关键代码
```java
private void insertSort(int[] array)
{
    int toInsert;
    for (int i = 1; i < array.length; i++)
    {
        // 缓存要插入的元素
        toInsert = array[i];
        // 遍历前面已经排序要的序列
        int j = i - 1;
        // 如果前面的一个元素比要插入的元素大,就将这个大的元素后移一格
        while (j >= 0 && array[j] > toInsert)
        {
            // 将比要插入的元素大的元素全部向后移动一格
            array[j + 1] = array[j];
            // 比较下一个格
            j--;
        }
        //
        array[j + 1] = toInsert;
    }
}
```