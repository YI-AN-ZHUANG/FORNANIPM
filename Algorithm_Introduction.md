# 演算法簡介

## 目錄
- [什麼是演算法](#什麼是演算法)
- [演算法特性](#演算法特性)
- [常見演算法類型](#常見演算法類型)
- [時間複雜度](#時間複雜度)
- [空間複雜度](#空間複雜度)
- [演算法設計方法](#演算法設計方法)
- [實際應用](#實際應用)

## 什麼是演算法

演算法（Algorithm）是一系列解決特定問題的明確步驟或指令。它是計算機科學的核心概念，用於解決各種計算問題。

### 演算法的基本要素
- **輸入**：演算法接收的數據
- **輸出**：演算法產生的結果
- **明確性**：每個步驟都必須清楚明確
- **有限性**：演算法必須在有限步驟內結束
- **有效性**：每個步驟都必須可行

## 演算法特性

### 正確性
- 演算法必須產生正確的結果
- 能夠處理所有有效的輸入

### 效率
- **時間效率**：執行速度要快
- **空間效率**：使用記憶體要少

### 可讀性
- 程式碼容易理解和維護
- 有適當的註解和文檔

## 常見演算法類型

### 1. 搜尋演算法

#### 線性搜尋 (Linear Search)
```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```
- **時間複雜度**：O(n)
- **適用場景**：未排序的資料

#### 二元搜尋 (Binary Search)
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```
- **時間複雜度**：O(log n)
- **適用場景**：已排序的資料

### 2. 排序演算法

#### 氣泡排序 (Bubble Sort)
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
```
- **時間複雜度**：O(n²)
- **空間複雜度**：O(1)

#### 快速排序 (Quick Sort)
```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```
- **時間複雜度**：平均 O(n log n)，最壞 O(n²)
- **空間複雜度**：O(log n)

### 3. 圖論演算法

#### 深度優先搜尋 (DFS)
```python
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    visited.add(start)
    print(start)
    for neighbor in graph[start]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)
```

#### 廣度優先搜尋 (BFS)
```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)
    
    while queue:
        vertex = queue.popleft()
        print(vertex)
        for neighbor in graph[vertex]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

### 4. 動態規劃

#### 費波那契數列
```python
def fibonacci(n):
    if n <= 1:
        return n
    dp = [0] * (n + 1)
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    return dp[n]
```

## 時間複雜度

### 常見時間複雜度
- **O(1)**：常數時間
- **O(log n)**：對數時間
- **O(n)**：線性時間
- **O(n log n)**：線性對數時間
- **O(n²)**：平方時間
- **O(2ⁿ)**：指數時間

### 時間複雜度比較
| 複雜度 | 名稱 | 範例 |
|--------|------|------|
| O(1) | 常數 | 陣列存取 |
| O(log n) | 對數 | 二元搜尋 |
| O(n) | 線性 | 線性搜尋 |
| O(n log n) | 線性對數 | 合併排序 |
| O(n²) | 平方 | 氣泡排序 |
| O(2ⁿ) | 指數 | 遞迴費波那契 |

## 空間複雜度

### 空間複雜度類型
- **O(1)**：常數空間
- **O(n)**：線性空間
- **O(n²)**：平方空間

### 空間複雜度考量
- 演算法使用的額外記憶體
- 遞迴呼叫的堆疊空間
- 暫存變數的記憶體使用

## 演算法設計方法

### 1. 分治法 (Divide and Conquer)
- 將問題分解為子問題
- 遞迴解決子問題
- 合併子問題的解

**範例**：合併排序、快速排序

### 2. 貪婪法 (Greedy)
- 在每個步驟選擇最佳選項
- 不考慮全局最優解
- 通常快速但可能不是最佳解

**範例**：Dijkstra演算法、Huffman編碼

### 3. 動態規劃 (Dynamic Programming)
- 將問題分解為重疊子問題
- 儲存子問題的解
- 避免重複計算

**範例**：最長公共子序列、背包問題

### 4. 回溯法 (Backtracking)
- 系統性地嘗試所有可能解
- 當發現無效解時回溯
- 用於組合優化問題

**範例**：N皇后問題、數獨求解

## 實際應用

### 網路應用
- **路由演算法**：尋找最佳網路路徑
- **搜尋引擎**：網頁排名和搜尋
- **社交網路**：推薦系統

### 資料處理
- **資料庫查詢**：索引和搜尋
- **大數據分析**：MapReduce
- **機器學習**：訓練演算法

### 圖形處理
- **圖像壓縮**：JPEG、PNG
- **視覺化**：圖形繪製演算法
- **遊戲開發**：路徑尋找

### 密碼學
- **加密演算法**：AES、RSA
- **雜湊函數**：SHA、MD5
- **數位簽章**：DSA、ECDSA

---

## 結語

演算法是計算機科學的基礎，掌握演算法不僅能提高程式設計能力，也能培養邏輯思維和問題解決能力。在實際開發中，選擇合適的演算法往往比寫出程式碼更重要。

好的演算法應該具備正確性、效率、可讀性等特性，並在時間複雜度和空間複雜度之間找到平衡。隨著技術發展，新的演算法不斷出現，但基礎的演算法設計原則始終是重要的。

---

*本文檔最後更新：2024年*
*參考資料：演算法教科書、線上課程、技術文檔等*
