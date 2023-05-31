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

##給一個int a[20]已排序的陣列，請寫一個function(a, size, b) 能依照參數b(b = 0~4)別印出該區間的數字，
且不包含a陣列內的元素，例如 b =0, 印出0~99 b = 1, 印出100~199 

```
void function(int *a, int size, int b){
    int *ptr = a;
    int i;
    //找到一個大於等於 b * 100 的元素
    while (*ptr < b * 100) {
        ptr++;
    }
    //從b*100 ~ ( b + 1 ) * 100 中，如果有找到陣列的數跳過，否則打印
    for (i = b*100; i<(b+1)*100; i++) {
        if (*ptr == i){
            ptr++;
        }
        else{
            printf("%d\n", i);
        }
    }
}

```

##尋找一個單項linkedlist中的資料，其中每個節點包含兩個資料，尋找的函數輸入是兩個資料的value，輸出是其索引

```
#include <iostream>

struct ListStruct {
    unsigned int DataH;
    unsigned int DataL;
    unsigned int NextPtr;
};

struct ListStruct ListArray[1000];

#define NULL 0xFFFF

unsigned int ListHead = 0;

unsigned int findEntry(unsigned int DATA_A, unsigned int DATA_B) {
    
    unsigned int currentEntry = ListHead;

    while (currentEntry != NULL) {
        if (ListArray[currentEntry].DataH == DATA_A && 
        ListArray[currentEntry].DataL == DATA_B) {
            return currentEntry;
        }
        currentEntry = ListArray[currentEntry].NextPtr;
    }

    return NULL; // 找不到符合條件的節點
}

int main() {

    ListArray[0].DataH = 1;
    ListArray[0].DataL = 1;
    ListArray[0].NextPtr = 1;
    
    ListArray[1].DataH = 2;
    ListArray[1].DataL = 2;
    ListArray[1].NextPtr = NULL;

    unsigned int result = findEntry(1, 1);
    if (result != NULL) {
        std::cout << "Entry found at index " << result << std::endl;
    } else {
        std::cout << "Entry not found" << std::endl;
    }

    return 0;
}
```

https://hackmd.io/@jQSlhiN3QaGkugpbD4NDAA/rkvNkyQfi
