# searching-arrays
🔍 Linear &amp; Binary Search in Java | Tutoring notes by Omphemetse Nkge

---

## 📌 Overview

**Searching** is the process of looking for a specific element in an array — for example, finding whether a certain score exists in a list. This module covers two fundamental search techniques:

| Technique | Best For | Requires Sorted Array? |
|-----------|----------|------------------------|
| 🔵 Linear Search | Small / unsorted arrays | ❌ No |
| 🟢 Binary Search | Large / sorted arrays | ✅ Yes |

---

## 🧠 Table of Contents

- [Components Needed to Search](#-components-needed-to-search)
- [Asymptotic Notation](#-asymptotic-notation)
- [Linear Search](#-linear-search--sequential-search)
- [Binary Search](#-binary-search--half-interval-search)
- [Comparison: Linear vs Binary](#-comparison-linear-vs-binary-search)
- [Exercises](#-exercises)

---

## 🛠️ Components Needed to Search

To search an element in an array, you need:

1. 📋 The **array** containing the elements
2. 📏 The **length** of the array
3. 🔑 The **key / search item** you are looking for

> Both techniques return the **index** of the found value, or `-1` if not found.

---

## ⏱️ Asymptotic Notation

Asymptotic notation describes the **amount of time** required to complete a process.

| Case | Description |
|------|-------------|
| **Best Case** | Minimum time — determines how fast the algorithm can be (at least) |
| **Average Case** | Expected time on average over all possible inputs |
| **Worst Case** | Maximum time — determines how slow the algorithm can be (at most) |

---

## 🔵 Linear Search / Sequential Search

### What is it?
Linear search checks **every element one at a time, in sequence**, until the target is found. It is the simplest search algorithm — a special case of the **Brute-Force** approach.

### How it Works

```
Array: [35, 17, 27, 42, 5]
Search for: 27

Step 1: Compare 27 with list[0] = 35 → ❌ Not found
Step 2: Compare 27 with list[1] = 17 → ❌ Not found
Step 3: Compare 27 with list[2] = 27 → ✅ Found! Return index 2
```

### ⚠️ Unsuccessful Search
```
Search for: 10
→ Compared with every element in the array
→ No match found → return -1 (Unsuccessful)
```

### Efficiency Analysis

| Case | Description | Notation |
|------|-------------|----------|
| **Best** | Item is the **first** element — 1 comparison | O(1) |
| **Average** | Item is somewhere in the middle — n/2 comparisons | O(n) |
| **Worst** | Item is **last** or **not in array** — n comparisons | O(n) |

> 💡 Linear Search is **not efficient for large arrays**. On average, it checks half the array.

### Implementation

```java
// Version 1 — Clean
public class LinearSearch {
    public static int linearSearch(int[] list, int key) {
        for (int i = 0; i < list.length; i++) {
            if (key == list[i])
                return i;
        }
        return -1;
    }
}

// Version 2 — With boolean flag
public int seqSearch(int[] array, int searchItem) {
    boolean found = false;
    int i = 0;

    for (i = 0; i < array.length; i++) {
        if (array[i] == searchItem) {
            found = true;
            break;
        }
    }

    if (found)
        return i;
    else
        return -1;
}
```

---

## 🟢 Binary Search / Half-Interval Search

### What is it?
Binary search finds an element in a **sorted array** by repeatedly **halving** the search space. It compares the key with the **middle element** each time. A special case of the **Divide and Conquer** algorithm.

> ⚠️ **Important:** The array MUST be sorted before using binary search!

### How it Works

```
Array (sorted): [2, 5, 13, 27, 38, 51, 64, 75, 89, 99]
Search for: 75

Step 1: Middle = index 4 → value 38. Is 75 > 38? ✅ → Search RIGHT half
Step 2: Middle = index 7 → value 75. Is 75 = 75? ✅ → FOUND! Return index 7
```

### Binary Search Logic

```
Compare key with middle element:
  ✅ key == middle      → Found! Return index
  ⬅️ key < middle       → Search LEFT (first half)
  ➡️ key > middle       → Search RIGHT (second half)
  🚫 No elements left  → Not found, return -1
```

### Efficiency Analysis

| Case | Description | Notation |
|------|-------------|----------|
| **Best** | Key is at the **middle** on first check | O(1) |
| **Average** | Logarithmic comparisons | O(log n) |
| **Worst** | Key at start/end or not in array | O(log n) |

> 💡 Binary Search is **much faster** than Linear Search for large sorted arrays.

### Implementation

```java
public int binarySearch(int[] array, int arrayLength, int searchItem) {
    int firstIndex = 0;
    int lastIndex = arrayLength - 1;
    int midIndex;
    boolean found = false;

    while (firstIndex <= lastIndex && !found) {
        midIndex = (firstIndex + lastIndex) / 2;

        if (array[midIndex] == searchItem)
            found = true;
        else if (array[midIndex] > searchItem)
            lastIndex = midIndex - 1;   // Search left half
        else
            firstIndex = midIndex + 1;  // Search right half
    }

    if (found)
        return midIndex;
    else
        return -1;
}
```

---

## ⚖️ Comparison: Linear vs Binary Search

| Feature | Linear Search 🔵 | Binary Search 🟢 |
|---------|-----------------|-----------------|
| **Array must be sorted** | ❌ No | ✅ Yes |
| **Best case** | O(1) | O(1) |
| **Average case** | O(n) | O(log n) |
| **Worst case** | O(n) | O(log n) |
| **Best used when** | Array is **short** or **unsorted** | Array is **long** and **sorted** |
| **Worst used when** | Array is **long** | Array is **short** or **unsorted** |
| **Algorithm type** | Brute-Force | Divide & Conquer |

> 📌 **Rule of Thumb:** If the array has more than 8 elements, **Binary Search is faster**.

---

## 🧩 Exercises

### Exercise – Analyse Scores
Write a program that:
- Reads an **unspecified number** of scores from the user
- Determines how many scores are **above or equal to the average**
- Determines how many scores are **below the average**
- Accepts a **negative number** to signal end of input
- Assumes a **maximum of 100 scores**

---

## 📬 Contact & Tutoring

| | |
|--|--|
| **Tutor** | Omphemetse Nkge |
| **Module** | Programming Fundamentals |
| **Topic** | Searching Arrays |

> *"Binary search doesn't just find answers faster — it teaches you to think smarter."*
> — Omphemetse Nkge
