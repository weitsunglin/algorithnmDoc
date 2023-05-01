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
#include <iostream>
#include <vector>

using namespace std;

void SieveOfEratosthenes(int n)
{
    vector<bool> prime(n + 1, true);
    for (int p = 2; p * p <= n; p++) {
        if (prime[p] == true) {
            for (int i = p * p; i <= n; i += p)
                prime[i] = false;
        }
    }

    for (int p = 2; p <= n; p++)
        if (prime[p])
            cout << p << " ";
}

int main()
{
    int n = 30;
    cout << "Following are the prime numbers smaller than or equal to " << n << endl;
    SieveOfEratosthenes(n);
    return 0;
}

```

## 0/1 背包問題

```
content

```
