## Two Sum

輸入: 一個目標值

輸出: 相加等於目標值的兩數索引

```
#include <iostream>
#include <unordered_map>
#include <vector>

std::vector<int> twoSum(std::vector<int>& nums, int target) {
    std::unordered_map<int, int> hash;
    for (int i = 0; i < nums.size(); i++) {
        int complement = target - nums[i];
        if (hash.find(complement) != hash.end()) {
            return {hash[complement], i};
        }
        hash[nums[i]] = i;
    }
    return {};
}

int main() {
    std::vector<int> vec = {2, 7, 11, 15};
    int target = 9;
    std::vector<int> result = twoSum(vec, target);
    if (!result.empty()) {
        std::cout << "Indices: " << result[0] << ", " << result[1] << std::endl;
    } else {
        std::cout << "No solution found." << std::endl;
    }
    return 0;
}

```

## 埃拉托斯特尼篩法

```
content

```

## 0/1 背包問題

```
content

```
