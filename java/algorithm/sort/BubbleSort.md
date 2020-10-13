# 1.1 冒泡排序

## 关键代码
```java
private void bubbleSort(int[] array)
{
    int temp;
    // 每次讲一个最大的元素移动到最后
    for (int i = 0; i < array.length; i++)
    {
        for (int j = 0; j < array.length - i - 1; j++)
        {
            // 比较如果前面的比后面的大,则将大的数交换到后面
            if (array[j] > array[j + 1])
            {
                temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }
}
```