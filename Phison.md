## 給一個int a[20]已排序的陣列，請寫一個function(a, size)能印出0~500的數字，且不包含a陣列內的元素


```
void function(int* a, int size) {
    int* ptr = a;
    for (int i = 0; i <= 10; i++) {
        if (*ptr == i) {
            ptr++;
        } else {
            printf("%d ", i);
        }
    }
}

```
