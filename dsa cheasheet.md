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
📌 LeetCode Problems Covered

Longest Substring Without Repeating Characters

Key Idea: Use a sliding window + HashMap (or array) to track characters and their last seen positions.

Pattern: Strings, HashMap, two-pointer window adjustment.

Similar Problems:

Longest Substring with At Most K Distinct Characters

Substring with Concatenation of All Words

Minimum Window Substring

Key Idea: Sliding window with character frequency map. Expand right pointer to include required chars, shrink left pointer to get minimum length.

Pattern: Strings, HashMap, sliding window with min length tracking.

Similar Problems:

Smallest Substring of All Characters

Permutation in String

First Unique Character in a String

Key Idea: Store frequencies in a HashMap or array, then find the first char with frequency = 1.

Mistake to Avoid: Your queue-based approach missed updating frequencies.

Similar Problems:

Find the Difference

Ransom Note

Intersection of Two Arrays II

Approach 1: HashMap to store frequencies from one array, then match with second array.

Approach 2 (Two-Pointer): Sort both arrays, move pointers based on comparison.

Pattern: Arrays, HashMap, sorting + two pointers.

Similar Problems:

Intersection of Two Arrays I

Find Common Elements in Three Sorted Arrays

📌 Java Concepts Discussed

HashMap with ASCII as key

Use map.put((int) ch, value);

(int) ch gives ASCII value of character.

Queue in Java (Collection Framework)

Common Implementations: LinkedList, PriorityQueue, ArrayDeque

Common Methods:

add(e), offer(e) → insert

poll() → remove head or return null

remove() → remove head or throw exception if empty

peek() → get head without removing

isEmpty() → check if empty

📌 Problem-Solving Patterns to Practice

Sliding Window: When dealing with substrings/subarrays and need optimal O(n) time.

Two Pointers: When arrays are sorted or can be sorted for easier comparison.

HashMap Frequency Counting: When tracking occurrences of elements for matches.

Queue for Order Tracking: When needing FIFO-based processing of indexes/elements.
