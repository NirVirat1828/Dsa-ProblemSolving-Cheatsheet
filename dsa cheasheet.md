### **1\. Reverse a String (O(n))**

* **Logic:** Two-pointer method → `left=0`, `right=n-1`, swap until `left < right`.

* **Key Point:** No nested loops, single pass.

* **Java Tip:** Convert string to `char[]` for mutability.

java  
CopyEdit  
`while (left < right) {`  
    `char temp = arr[left];`  
    `arr[left] = arr[right];`  
    `arr[right] = temp;`  
    `left++; right--;`  
`}`

---

### **2\. Convert String to Lowercase**

* Use `toLowerCase()`:

java  
CopyEdit  
`String lower = str.toLowerCase();`  
`String lowerLocale = str.toLowerCase(Locale.ENGLISH); // safer for fixed rules`

---

### **3\. Palindrome Check**

* No need to create a `char[]` — just use `charAt()` with two pointers.

* For case-insensitive check ignoring spaces/punctuation:

java  
CopyEdit  
`String cleaned = s.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();`

* Then apply two-pointer check.

---

### **4\. Remove Non-Alphanumeric Characters**

* **Regex:** `[^a-zA-Z0-9]` → keeps only letters and digits.

* Add space inside brackets to keep spaces:

java  
CopyEdit  
`str.replaceAll("[^a-zA-Z0-9 ]", "");`

* For all languages:

java  
CopyEdit  
`str.replaceAll("[^\\p{L}\\p{N}]", "");`

---

### **5\. Two Sum Problem**

* **O(n²):** Nested loops — slow.

* **O(n):** Use HashMap for complement lookup.

java  
CopyEdit  
`HashMap<Integer, Integer> map = new HashMap<>();`  
`for (int i = 0; i < nums.length; i++) {`  
    `int comp = target - nums[i];`  
    `if (map.containsKey(comp)) return new int[]{map.get(comp), i};`  
    `map.put(nums[i], i);`  
`}`

---

### **6\. Maximum Subarray (Kadane’s Algorithm)**

* **Optimal O(n)** time, **O(1)** space.

java  
CopyEdit  
`int maxSum = nums[0], currSum = nums[0];`  
`for (int i = 1; i < nums.length; i++) {`  
    `currSum = Math.max(nums[i], currSum + nums[i]);`  
    `maxSum = Math.max(maxSum, currSum);`  
`}`

* Tracks best sum ending at each position.

---

### **7\. Rotate Array by k Steps (O(n))**

* Reverse-based method:

java  
CopyEdit  
`k %= n;`  
`reverse(nums, 0, n-1);`  
`reverse(nums, 0, k-1);`  
`reverse(nums, k, n-1);`

* **Why:** Swapping first/last repeatedly doesn’t rotate correctly.

---

### **8\. Set Matrix Zeroes (O(1) space)**

* Use first row/col as markers.

* Steps:

  1. Record if first row/col need zeroing.

  2. Mark zeros in first row/col for others.

  3. Apply zeros based on markers.

  4. Zero first row/col if needed.

java  
CopyEdit  
`// marker setting`  
`if (matrix[i][j] == 0) {`  
    `matrix[i][0] = 0;`  
    `matrix[0][j] = 0;`  
`}`

---

## **Common Patterns You Practiced**

* **Two-pointer technique** (reverse string, palindrome check)

* **String cleaning with regex**

* **HashMap lookups for O(n) search**

* **Dynamic Programming** (Kadane’s)

* **In-place array rotation**

* **Matrix marker trick for O(1) space**

---

If you keep this list and **write each code from scratch at least twice** in the next week, you’ll remember both the logic and the syntax for similar problems in the future.
# 📚 LeetCode Problem Patterns for Mastery

To truly remember both the logic and syntax for common coding problems, write solutions for each problem from scratch at least **twice** in the next week. This focused repetition will help you internalize key techniques and avoid common mistakes in future interviews or coding challenges.

---

## 📌 Problems & Key Patterns

### 1. Longest Substring Without Repeating Characters

- **Core Idea:**  
  Use a **sliding window** and a `HashMap` (or array) to track each character's last seen position.
- **Pattern:**  
  Strings, HashMap, two-pointer window adjustment.

**Practice Similar Problems:**
- Longest Substring with At Most K Distinct Characters
- Substring with Concatenation of All Words

---

### 2. Minimum Window Substring

- **Core Idea:**  
  Use a **sliding window** and a frequency map to cover all target characters.  
  Expand the right pointer to include required chars; shrink the left pointer to minimize window length.
- **Pattern:**  
  Strings, HashMap, sliding window with min length tracking.

**Practice Similar Problems:**
- Smallest Substring of All Characters
- Permutation in String

---

### 3. First Unique Character in a String

- **Core Idea:**  
  Store character frequencies in a `HashMap` or array, then scan for the first char with frequency == 1.
- **Mistake to Avoid:**  
  If using a queue, remember to update frequencies correctly to avoid stale results.

**Practice Similar Problems:**
- Find the Difference
- Ransom Note

---

### 4. Intersection of Two Arrays II

- **Approach 1:**  
  Use a `HashMap` to store frequencies from one array, then match and reduce with the second array.
- **Approach 2 (Two-Pointer):**  
  Sort both arrays, then move pointers to collect matches efficiently.

- **Pattern:**  
  Arrays, HashMap, sorting + two pointers.

**Practice Similar Problems:**
- Intersection of Two Arrays I
- Find Common Elements in Three Sorted Arrays

---

## 📌 Java Concepts & Techniques

### HashMap with ASCII Keys
- Use: `map.put((int) ch, value);`
- `(int) ch` converts a character to its ASCII integer value for direct mapping.

### Queue Implementations in Java
- Common: `LinkedList`, `PriorityQueue`, `ArrayDeque`
- Methods:
  - `add(e)`, `offer(e)` – Insert
  - `poll()` – Remove head (returns null if empty)
  - `remove()` – Remove head (throws exception if empty)
  - `peek()` – Get head without removing
  - `isEmpty()` – Check if empty

---

## 📌 Problem-Solving Patterns to Practice

| Pattern                  | When to Use                | Example Problems                              |
|--------------------------|----------------------------|-----------------------------------------------|
| **Sliding Window**       | Substrings/subarrays, O(n) | Longest Substring Without Repeating Characters|
| **Two Pointers**         | Sorted arrays/comparison   | Intersection of Two Arrays II                 |
| **HashMap Frequency**    | Counting occurrences       | First Unique Character in String              |
| **Queue (FIFO Order)**   | Track processing order     | Level-order traversal, First Unique Char      |

---

## 📝 Tips for Mastery

- **Write from scratch, twice:** Repetition is the key to solidifying your understanding.
- **Track mistakes:** Note any common pitfalls (e.g., forgetting to update frequencies).
- **Practice variants:** Tackle similar problems to reinforce pattern recognition.
- **Review Java collections:** Understand implementation differences and method behaviors for real-world coding.

---

**Happy Coding!** 🚀

Queue for Order Tracking: When needing FIFO-based processing of indexes/elements.
# 🔹 Binary Search Cheatsheet for LeetCode-Style Problems

---

## 1. Classic Binary Search

**Pattern:** Sorted array → search for element.

**Code skeleton:**
```cpp
while (left <= right) {
    int mid = left + (right - left) / 2;
    if (nums[mid] == target) return mid;
    else if (nums[mid] < target) left = mid + 1;
    else right = mid - 1;
}
```
**Trick:** Always move `left = mid + 1` or `right = mid - 1` → avoid infinite loop.

---

## 2. Find First/Last Occurrence (Duplicates)

**Pattern:** Sorted array with duplicates → find boundary.

- **First occurrence:**  
  If `nums[mid] == target`, move `right = mid - 1`.

- **Last occurrence:**  
  If `nums[mid] == target`, move `left = mid + 1`.

---

## 3. Find Minimum in Rotated Sorted Array

**Pattern:** Array is rotated, no duplicates.

**Trick:** Compare `nums[mid]` with `nums[right]`.

- If `nums[mid] > nums[right]` → min is in right half → `left = mid + 1`.
- Else → min is in left half → `right = mid`.

**End:** `left` is min index.

---

## 4. Search in Rotated Sorted Array ([LeetCode 33](https://leetcode.com/problems/search-in-rotated-sorted-array/))

Pivot divides array into 2 sorted halves.

**Two approaches:**
- Find pivot → then normal binary search in correct half.
- Modified binary search (no pivot):

```cpp
if (nums[left] <= nums[mid]) { // left half sorted
    if (nums[left] <= target && target < nums[mid])
        right = mid - 1;
    else
        left = mid + 1;
} else { // right half sorted
    if (nums[mid] < target && target <= nums[right])
        left = mid + 1;
    else
        right = mid - 1;
}
```

---

## 5. Find Peak Element ([LeetCode 162](https://leetcode.com/problems/find-peak-element/))

Array has ups & downs, find any peak.

**Trick:** Compare `nums[mid]` with `nums[mid+1]`.

- If `nums[mid] > nums[mid+1]` → peak on left → `right = mid`.
- Else → peak on right → `left = mid + 1`.

**End:** `left` is peak index.

---

## 6. First Bad Version ([LeetCode 278](https://leetcode.com/problems/first-bad-version/))

Boolean sequence `[false, false, …, true, true]`.

**Trick:** Search for first true.

- If `isBadVersion(mid)` → `right = mid`.
- Else → `left = mid + 1`.

**End:** `left` is first bad.

---

## 7. Binary Search on Answer (Range Problems)

When array not directly sorted but answer space is monotonic (true/false).

**Examples:**  
Minimum days to complete jobs.  
Capacity to ship packages.

**Template:**
```cpp
while (left < right) {
    int mid = left + (right - left) / 2;
    if (check(mid)) right = mid;
    else left = mid + 1;
}
```

---

## 🔑 Key Rules to Remember

- Always avoid infinite loop → use `mid + 1` or `mid - 1`.
- Think in terms of sorted halves.
- Check monotonic property (true/false switch).
- When searching boundary (first/last/minimum) → usually shrink `right = mid`.
- When searching exact element → shrink with ±1.

✅ If you keep these patterns in your head, **90% of binary search problems** (rotated arrays, peaks, bad version, duplicates, search space problems) can be solved quickly.

# LeetCode Matrix Problems Cheat Sheet

---

## 1. Spiral Matrix

**👉 Problem:** Print matrix elements in spiral order.

### Algorithm:

- Initialize 4 boundaries: `top=0`, `bottom=m-1`, `left=0`, `right=n-1`.
- Loop while `top <= bottom && left <= right`:
  - Traverse left → right (top row). `top++`.
  - Traverse top → bottom (right col). `right--`.
  - If still valid: traverse right → left (bottom row). `bottom--`.
  - If still valid: traverse bottom → top (left col). `left++`.
- Collect elements until all are visited.

### Snippet:
```java
while (top <= bottom && left <= right) {
    for (int j = left; j <= right; j++) res.add(matrix[top][j]);
    top++;
    for (int i = top; i <= bottom; i++) res.add(matrix[i][right]);
    right--;
    if (top <= bottom)
        for (int j = right; j >= left; j--) res.add(matrix[bottom][j]);
    bottom--;
    if (left <= right)
        for (int i = bottom; i >= top; i--) res.add(matrix[i][left]);
    left++;
}
```

---

## 2. Word Search (DFS + Backtracking)

**👉 Problem:** Find if a word exists in the grid.

### Algorithm:

- For each cell in the grid, start DFS if it matches first character.
- In DFS:
  - If out of bounds / mismatch → return false.
  - If all chars matched → return true.
  - Mark current cell as visited (temporarily change char).
  - Recurse in 4 directions.
  - Backtrack (restore char).
- Return true if any DFS succeeds.

### Snippet:
```java
boolean dfs(char[][] board, String word, int i, int j, int idx) {
    if (idx == word.length()) return true;
    if (i < 0 || j < 0 || i >= board.length || j >= board[0].length
        || board[i][j] != word.charAt(idx)) return false;
    
    char temp = board[i][j];
    board[i][j] = '#'; // mark visited
    
    boolean found = dfs(board, word, i+1,j,idx+1) ||
                    dfs(board, word, i-1,j,idx+1) ||
                    dfs(board, word, i,j+1,idx+1) ||
                    dfs(board, word, i,j-1,idx+1);
    
    board[i][j] = temp; // backtrack
    return found;
}
```

---

## 3. Rotate Image (90° Clockwise)

**👉 Problem:** Rotate n x n matrix in-place.

### Algorithm:

- Transpose the matrix (swap `matrix[i][j]` ↔ `matrix[j][i]`).
- Reverse each row.

### Snippet:
```java
// transpose
for (int i = 0; i < n; i++) {
    for (int j = i; j < n; j++) {
        int temp = matrix[i][j];
        matrix[i][j] = matrix[j][i];
        matrix[j][i] = temp;
    }
}
// reverse rows
for (int i = 0; i < n; i++) {
    for (int j = 0, k = n-1; j < k; j++, k--) {
        int temp = matrix[i][j];
        matrix[i][j] = matrix[i][k];
        matrix[i][k] = temp;
    }
}
```

---

## 📝 Quick Memory Hooks

- **Spiral Matrix** → "Boundaries shrink step by step."
- **Word Search** → "DFS + Backtrack, mark visited, restore later."
- **Rotate Image** → "Transpose + Reverse Rows."
