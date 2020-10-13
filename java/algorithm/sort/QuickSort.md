# 1.2 快速排序

# 关键代码
```java
private void quickSort(int[] array)
{
    quickSort(array, 0, array.length - 1);
}
private void quickSort(int[] array, int left, int right)
{
    if (left < right)
    {
        int splitIndex = divide(array, left, right);
        quickSort(array, left, splitIndex - 1);
        quickSort(array, splitIndex + 1, right);
    }
}
private int divide(int[] array, int left, int right)
{
    int splitPoint = array[left];
    int i = left;
    int j = right;
    while (i < j)
    {
        // 从右到左 找出比分割点小的元素
        while (j > i)
        {
            // 如果在右边找到比分割点小的数,结束查找
            if (array[j] < splitPoint)
            {
                break;
            }
            j--;
        }
        // 从左往右 找出比分割点大的元素
        while (i < j)
        {
            // 找到一个比分割点大的数,则结束查找
            if (array[i] > splitPoint)
            {
                break;
            }
            i++;
        }
        if (j > i)
        {
            swap(array, i, j);
            printSwap(array, i, j, left, right);;
        }
    }
    swap(array, left, i);
    printSwap(array, left, i, left, right);
    return i;
}
private void swap(int[] array, int i, int j)
{
    int temp = array[i];
    array[i] = array[j];
    array[j] = temp;
}
```