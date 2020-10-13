# 1.2 选择排序

# 关键代码
```java
private void selectSort(int[] array)
{
    // 选择排序法
    for (int i = 0; i < array.length; i++)
    {
        int maxIndex = 0;
        // 查找未排序区域中的最大值
        for (int j = 0; j < array.length - i; j++)
        {
            if (array[j] > array[maxIndex])
            {
                maxIndex = j;
            }
        }
        // 将最大的数换到后面
        // 缓存最后的数
        int temp = array[array.length - 1 - i];
        // 将大的数换到最后
        array[array.length - 1 - i] = array[maxIndex];
        // 将最后的数换到
        array[maxIndex] = temp;
    }
}
```