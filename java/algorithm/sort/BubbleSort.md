# 1.1 冒泡排序

## 关键代码
```java
private void bubbleSort(int[] array)
{
    int temp;
    // 每次能选出一个最大的元素到尾部
    for (int i = 0; i < array.length; i++)
    {
        for (int j = 0; j < array.length - i - 1; j++)
        {
            // 如果前面的大于后面的
            if (array[j] > array[j + 1])
            {
                temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
        // 打印这次排序的结果
        printSortingSteps(array, i);
    }
}
```