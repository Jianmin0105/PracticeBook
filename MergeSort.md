```java

Class MergeSort{
  public int[] mergeSort(int[] array) {
    if (array == null) {
      return array;
    }
    int[] helper = new int[array.length];
    mergeSort(array, helper, 0, array.length -1);
    return array;
  }

  public void mergeSort(int[] array, int[] helper, int left, int right) {

    // termination conditions
    if (left >= right) {
      return;
    }
    int mid = left + (right - left) / 2;
    // sort left half, sort right half, then merge 2 parts together
    mergeSort(array, helper, left, mid);
    mergeSort(array, helper, mid + 1, right);
    merge(array, helper, left, right);
  }

  public void merge(int[] array, int[] helper, int left, int right) {

    for (int i = left; i <= right; i++) {
      helper[i] = array[i];
    }

    int leftIndex = left;
    int mid = left + (right - left) / 2;
    int rightIndex = mid + 1;

    // merge 2 array in ascending order
    while (leftIndex <= mid && rightIndex <= right) {
      if (helper[leftIndex] <= helper[rightIndex]) {
        array[left++] = helper[leftIndex++];
      } else {
        array[left++] = helper[rightIndex++];
      }
    }

    while (leftIndex <= mid) {
      array[left++] = helper[leftIndex++];
    }
  }
}

```
