# 演算法大補包


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
#include <iostream>
#include <vector>
using namespace std;

// 0/1 背包問題的函數
int knapsack(int W, vector<int> wt, vector<int> val, int n) {
    vector<vector<int>> K(n + 1, vector<int>(W + 1));

    for (int i = 0; i <= n; i++) {
        for (int w = 0; w <= W; w++) {
            if (i == 0 || w == 0) {
                K[i][w] = 0;
            } else if (wt[i - 1] <= w) {
                K[i][w] = max(val[i - 1] + K[i - 1][w - wt[i - 1]], K[i - 1][w]);
            } else {
                K[i][w] = K[i - 1][w];
            }
        }
    }
    return K[n][W];
}

int main() {
    int W = 50;
    vector<int> val = {60, 100, 120};
    vector<int> wt = {10, 20, 30};
    int n = val.size();
    cout << "0/1 背包問題的最大價值: " << knapsack(W, wt, val, n) << endl;
    return 0;
}


```

## DFS

```
using System;
using System.Collections.Generic;

class Graph
{
    private int numVertices;

    private List<int>[] adjacencyList; //存放點的相鄰邊

    public Graph(int numVertices)
    {
        this.numVertices = numVertices;

        adjacencyList = new List<int>[numVertices];

        for (int i = 0; i < numVertices; i++)
        {
            adjacencyList[i] = new List<int>();
        }
    }

    public void AddEdge(int source, int destination)
    {
        adjacencyList[ source ].Add( destination );
    }



    public void DFS(int startVertex)
    {
        bool[] visited = new bool[numVertices];

        DFSUtil(startVertex, visited);
    }

    private void DFSUtil(int vertex, bool[] visited)
    {
        visited[vertex] = true;

        Console.Write(vertex + " ");

        foreach (int neighbor in adjacencyList[vertex])
        {
            if (!visited[neighbor])
            {
                DFSUtil(neighbor, visited);
            }
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        // 基於頂點數量建構圖
        Graph graph = new Graph(5);

        //加入邊
        graph.AddEdge(0, 1);
        graph.AddEdge(0, 2);
        graph.AddEdge(1, 3);
        graph.AddEdge(2, 3);
        graph.AddEdge(2, 4);
        graph.AddEdge(3, 4);

        Console.WriteLine("深度優先走訪结果:");

        graph.DFS(0);
    }
}

```
