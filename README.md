# 📚 Data Structures and Algorithms - Java Reference Guide

A comprehensive collection of commonly used DSA algorithms and data structure implementations in Java.

---

## 📋 Table of Contents

- [Basic Functions](#-basic-functions)
  - [Hello World & Input Operations](#hello-world--input-operations)
  - [Mathematical Functions](#mathematical-functions)
- [Array Operations](#-array-operations)
  - [Array Basics](#array-basics)
  - [Array Utility Functions](#array-utility-functions)
  - [Maximum Subarray Sum Algorithms](#maximum-subarray-sum-algorithms)
- [Searching Algorithms](#-searching-algorithms)
  - [Linear Search](#linear-search)
  - [Binary Search](#binary-search)
- [Sorting Algorithms](#-sorting-algorithms)
  - [Bubble Sort](#bubble-sort---on)
  - [Selection Sort](#selection-sort---on)
  - [Insertion Sort](#insertion-sort---on)
  - [Counting Sort](#counting-sort---on--k)
  - [Built-in Sorting](#built-in-sorting)
- [2D Arrays](#-2d-arrays)
- [String Operations](#-string-operations)
  - [String Basics](#string-basics)
  - [String Algorithms](#string-algorithms)
- [Bit Manipulation](#-bit-manipulation)
- [Main Method Examples](#-main-method-examples)
- [Complexity Analysis](#-complexity-analysis)

---

## 🔧 Basic Functions

### Hello World & Input Operations

```java
public static void PrintHelloworld() {
    System.out.print("Hello world");
}

public static void calculateSun() {
    Scanner sc = new Scanner(System.in);
    int a = sc.nextInt();
    int b = sc.nextInt();
    int sum = a + b;
    System.out.print("sum is : " + sum);
}
```

### Mathematical Functions

```java
// Sum calculation
public static void calculateNewSum(int num1, int num2) {
    int sum = num1 + num2;
    System.out.print("sum is : " + sum);
}

public static int NewSum(int num1, int num2) {
    int sum = num1 + num2;
    return sum;
}

// Swap two numbers
public static void Swap(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
    System.out.println("value of a is :" + a);
    System.out.println("value of b is :" + b);
}

// Product calculation
public static int Product(int a, int b) {
    int Product = a * b;
    return Product;
}

// Factorial calculation
public static int factorial(int n) {
    int f = 1;
    for(int i = 1; i <= n; i++) {
        f = f * i;
    }
    return f;
}

// Binomial coefficient
public static int bionomial(int n, int r) {
    int n_fact = factorial(n);
    int r_fact = factorial(r);
    int nr_fact = factorial(n-r);
    int b = n_fact/(r_fact * nr_fact);
    return b;
}

// Prime number check
public static boolean isPrime(int n) {
    if(n == 2) return true;
    for(int i = 2; i <= Math.sqrt(n); i++) {
        if(n % i == 0) return false;
    }
    return true;
}

// Print prime numbers in range
public static void PrimeRange(int n) {
    for(int i = 2; i <= n; i++) {
        if(isPrime(i)) {
            System.out.print(i);
        }
        System.out.println();
    }
}

// Number system conversions
public static void BintoDeci(int BinNum) {
    int pow = 0;
    int deci = 0;
    int Mynum = BinNum;
    while(BinNum > 0) {
        int lastdigit = BinNum % 10;
        deci = deci + (lastdigit * (int)Math.pow(2, pow));
        pow++;
        BinNum = BinNum / 10;
    }
    System.out.println("bin of this : " + Mynum + " deci is : " + deci);
}

public static void DecitoBin(int DeciNum) {
    int pow = 0;
    int bin = 0;
    int MyNum = DeciNum;
    while(DeciNum > 0) {
        int rem = DeciNum % 2;
        bin = bin + (rem * (int)Math.pow(10, pow));
        pow++;
        DeciNum = DeciNum / 2;
    }
    System.out.println("Deci of this : " + MyNum + " Bin is : " + bin);
}
```

---

## 📊 Array Operations

### Array Basics

```java
public static void Arrays() {
    int arr[] = new int[5];
    int arr1[] = {1, 2, 3, 4};
    String arr2[] = {"apple", "mango", "bannan"};
    
    for(int i = 0; i < arr1.length; i++) {
        System.out.print(arr1[i] + " ");
    }
    System.out.println();
    
    for(int i = 0; i < arr2.length; i++) {
        System.out.print(arr2[i] + " ");
    }
}

public static void Output() {
    int marks[] = new int[3];
    Scanner sc = new Scanner(System.in);
    marks[0] = sc.nextInt();
    marks[1] = sc.nextInt();
    marks[2] = sc.nextInt();
    
    System.out.println("marks of phy : " + marks[0]);
    System.out.println("marks of math : " + marks[1]);
    System.out.println("marks of chy : " + marks[2]);
    
    marks[2] = 100;
    System.out.println("marks of chy : " + marks[2]);
    System.out.println("length of arrays is : " + marks.length);
}

public static void update(int marks[]) {
    for(int i = 0; i < marks.length; i++) {
        marks[i] = marks[i] + 1;
    }
}
```

### Array Utility Functions

```java
// Get largest value
public static int getlargest(int numbers[]) {
    int largest = Integer.MIN_VALUE;
    for(int i = 0; i < numbers.length; i++) {
        if(largest < numbers[i]) {
            largest = numbers[i];
        }
    }
    return largest;
}

// Get smallest value
public static int getlowest(int numbers[]) {
    int lowest = Integer.MAX_VALUE;
    for(int i = 0; i < numbers.length; i++) {
        if(lowest > numbers[i]) {
            lowest = numbers[i];
        }
    }
    return lowest;
}

// Reverse array
public static void reverse(int numbers[]) {
    int start = 0; 
    int end = numbers.length-1;
    while(start < end) {
        int temp = numbers[end];
        numbers[end] = numbers[start];
        numbers[start] = temp;
        start++;
        end--;
    }
}

// Print all pairs
public static void pairs(int numbers[]) {
    int tp = 0;
    for(int i = 0; i < numbers.length; i++) {
        int curr = numbers[i];
        for(int j = i + 1; j < numbers.length; j++) {
            System.out.print("(" + curr + "," + numbers[j] + ")");
            tp++;
        }
        System.out.println();
    }
    System.out.print("total pairs is : " + tp);
}

// Print all subarrays
public static void SubArrays(int numbers[]) {
    int tp = 0;
    for(int i = 0; i < numbers.length; i++) {
        int start = numbers[i];
        for(int j = i+1; j < numbers.length; j++) {
            int end = numbers[j];
            for(int k = i; k < j; k++) {
                System.out.print(numbers[k] + " ");
                tp++;
            }
            System.out.println();
        }
        System.out.println();
    }
    System.out.print("total pairs of this subarrays : " + tp);
}
```

### Maximum Subarray Sum Algorithms

```java
// Brute force approach - O(n³)
public static void MaxSumSubArray(int numbers[]) {
    int currSum = 0;
    int MaxSum = Integer.MIN_VALUE;
    for(int i = 0; i < numbers.length; i++) {
        for(int j = i+1; j < numbers.length; j++) {
            currSum = 0;
            for(int k = i; k < j; k++) {
                currSum += numbers[k];
            }
            System.out.println("current sum is : "+currSum + " ");
            if(MaxSum < currSum) {
                MaxSum = currSum;
            }
            System.out.println();
        }
    }
    System.out.println("max sum is : " + MaxSum);
}

// Prefix sum approach - O(n²)
public static void MaxSubArrByPrefix(int numbers[]) {
    int currSum = 0;
    int MaxSum = Integer.MIN_VALUE;
    int Prefix[] = new int[numbers.length];
    
    Prefix[0] = numbers[0];
    for(int i = 1; i < Prefix.length; i++) {
        Prefix[i] = Prefix[i-1] + numbers[i];
    }
    
    for(int i = 0; i < numbers.length; i++) {
        for(int j = i+1; j < numbers.length; j++) {
            currSum = i == 0 ? Prefix[j] : Prefix[j] - Prefix[i-1];
            if(MaxSum < currSum) {
                MaxSum = currSum;
            }
        }
    }
    System.out.println("max sum is : " + MaxSum);
}

// Kadane's Algorithm - O(n)
public static void kadanes(int numbers[]) {
    int cs = 0;
    int ms = Integer.MIN_VALUE;
    
    for(int i = 0; i < numbers.length; i++) {
        cs = cs + numbers[i];
        if(cs < 0) {
            cs = 0;
        }
        ms = Math.max(cs, ms);
    }
    System.out.println("max sum is : " + ms);
}
```

---

## 🔍 Searching Algorithms

### Linear Search

```java
public static int linearSearch(int numbers[], int key) {
    for(int i = 0; i < numbers.length; i++) {
        if(numbers[i] == key) {
            return i;
        }
    }
    return -1;
}

// String linear search
public static int Menu(String menu[], String key) {
    for(int i = 0; i < menu.length; i++) {
        if(menu[i].equals(key)) {
            return i;
        }
    }
    return -1;
}
```

### Binary Search

```java
public static int BinearySearch(int numbers[], int key) {
    int start = 0; 
    int end = numbers.length-1;
    
    while(start <= end) {
        int mid = (start + end)/2;
        
        if(numbers[mid] == key) {
            return mid;
        }
        if(numbers[mid] < key) {
            start = mid + 1;
        } else {
            end = mid - 1;
        }
    }
    return -1;
}
```

---

## 📈 Sorting Algorithms

### Bubble Sort - O(n²)

```java
public static void BubbleSorting(int numbers[]) {
    for(int i = 0; i < numbers.length-1; i++) {
        for(int j = 0; j < numbers.length-1-i; j++) {
            if(numbers[j] > numbers[j+1]) {
                int temp = numbers[j];
                numbers[j] = numbers[j+1];
                numbers[j+1] = temp;
            }
        }
    }
}
```

### Selection Sort - O(n²)

```java
public static void SelectSorting(int numbers[]) {
    for(int i = 0; i < numbers.length-1; i++) {
        int minPos = i;
        for(int j = i+1; j < numbers.length; j++) {
            if(numbers[minPos] > numbers[j]) {
                minPos = j;
            }
        }
        int temp = numbers[minPos];
        numbers[minPos] = numbers[i];
        numbers[i] = temp;
    }
}
```

### Insertion Sort - O(n²)

```java
public static void InsertionSort(int numbers[]) {
    for(int i = 1; i < numbers.length; i++) {
        int curr = numbers[i];
        int pre = i-1;
        // Finding correct position to insert
        while(pre >= 0 && numbers[pre] > curr) {
            numbers[pre+1] = numbers[pre];
            pre--;
        }
        // Insertion
        numbers[pre+1] = curr;
    }
}
```

### Counting Sort - O(n + k)

```java
public static void CountSorting(int numbers[]) {
    int largest = Integer.MIN_VALUE;
    for(int i = 0; i < numbers.length; i++) {
        largest = Math.max(largest, numbers[i]);
    }
    
    int count[] = new int[largest+1];
    for(int i = 0; i < numbers.length; i++) {
        count[numbers[i]]++;
    }
    
    // Sorting
    int j = 0;
    for(int i = 0; i < count.length; i++) {
        while(count[i] > 0) {
            numbers[j] = i;
            j++;
            count[i]--;
        }
    }
}
```

### Built-in Sorting

```java
// Ascending order
Arrays.sort(numbers);

// Sort specific range
Arrays.sort(numbers, 0, 3);

// Descending order (requires Integer array)
Integer numbers[] = {5, 4, 1, 3, 2};
Arrays.sort(numbers, Collections.reverseOrder());

// Descending order for specific range
Arrays.sort(numbers, 1, 4, Collections.reverseOrder());
```

---

## 🎯 2D Arrays

### Basic 2D Array Operations

```java
public static void TowDArrays() {
    int matrix[][] = new int[3][3];
    int n = matrix.length; 
    int m = matrix[0].length;
    
    Scanner sc = new Scanner(System.in);
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < m; j++) {
            matrix[i][j] = sc.nextInt();
        }
    }
    
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < m; j++) {
            System.out.print(matrix[i][j] + " ");
        }
        System.out.println();
    }
}

// Search in 2D array
public static boolean SearchTwoDarray(int matrix[][], int key) {
    for(int i = 0; i < matrix.length; i++) {
        for(int j = 0; j < matrix[0].length; j++) {
            if(matrix[i][j] == key) {
                System.out.print("key is found at : " + "(" + i + "," + j + ")");
                return true;
            }
        }
    }
    System.out.print("key is not found");
    return false;
}
```

---

## 📝 String Operations

### String Basics

```java
public static void newStrings() {
    String str1 = "vishal";
    String str2 = new String("hgfds");
    
    // String concatenation
    String firstname = "vishal";
    String lastname = "rajput";
    String fullname = firstname + lastname;
    
    // Character access
    System.out.println(fullname.charAt(3)); // Output: 'h'
    
    // String traversal
    for(int i = 0; i < fullname.length(); i++) {
        System.out.print(fullname.charAt(i) + " ");
    }
}
```

### String Algorithms

```java
// Palindrome check
public static boolean palindrome(String str) {
    for(int i = 0; i < str.length()/2; i++) {
        int n = str.length();
        if(str.charAt(i) != str.charAt(n-1-i)) {
            return false;
        }
    }
    return true;
}

// Shortest path calculation
public static int getShortestPath(String path) {
    int x = 0; 
    int y = 0;
    for(int i = 0; i < path.length(); i++) {
        char dir = path.charAt(i);
        if(dir == 'S') y--;
        else if(dir == 'N') y++;
        else if(dir == 'W') x--;
        else x++;
    }
    int X2 = x*x;
    int Y2 = y*y;
    return (int)Math.sqrt(X2 + Y2);
}

// Custom substring implementation
public static String SubString(String str, int si, int ei) {
    String substr = "";
    for(int i = si; i < ei; i++) {
        substr += str.charAt(i);
    }
    return substr;
}

// Find largest string
public static String largestString(String fruits[]) {
    String largest = fruits[0];
    for(int i = 0; i < fruits.length; i++) {
        if(largest.compareTo(fruits[i]) < 0) {
            largest = fruits[i];
        }
    }
    return largest;
}

// Convert to title case
public static String toUpperCase(String str) {
    StringBuilder sb = new StringBuilder();
    sb.append(Character.toUpperCase(str.charAt(0)));
    
    for(int i = 1; i < str.length(); i++) {
        if(str.charAt(i - 1) == ' ') {
            sb.append(Character.toUpperCase(str.charAt(i)));
        } else {
            sb.append(str.charAt(i));
        }
    }
    return sb.toString();
}

// String compression
public static String Compressed(String str) {
    StringBuilder newstr = new StringBuilder("");
    int count = 1;
    
    for(int i = 0; i < str.length(); i++) {
        if(i < str.length()-1 && str.charAt(i) == str.charAt(i+1)) {
            count++;
        } else {
            newstr.append(str.charAt(i));
            newstr.append(count);
            count = 1;
        }
    }
    return newstr.toString();
}

// String utility methods
public static void stringUtilities() {
    String str1 = "hello";
    String str2 = "world";
    String str3 = "Hello";
    String str4 = "           hello";
    
    System.out.println(str1.concat(" ").concat(str2));
    System.out.println(str1.equals(str3));  // false
    System.out.println(str1.equalsIgnoreCase(str3));  // true
    System.out.println("compare two string : " + str1.compareTo(str2));
    System.out.println("get to upper case : " + str1.toUpperCase());
    System.out.println("use trim methode : " + str4.trim());
    System.out.println("use replace : " + str1.replace("hello", "wello"));
    System.out.println("check substring exits or not : " + str1.contains("java"));
}
```

---

## 🔢 Bit Manipulation

### Basic Bitwise Operations

```java
public static void bitwiseOperators(int a, int b) {
    System.out.println("Binary AND (&): " + (a & b));
    System.out.println("Binary OR (|): " + (a | b));
    System.out.println("Binary XOR (^): " + (a ^ b));
    System.out.println("Binary One's Complement (~a): " + (~a));
}

// Shift operations
public static void LeftandRightShift(int x, int y) {
    // Left shift: x << y = x * 2^y
    System.out.println("left shift is : " + (x << y));
    
    // Right shift: x >> y = x / 2^y
    System.out.println("right shift is : " + (x >> y));
}

// Check if number is even or odd
public static void oddandevenNuminBit(int n) {
    int binMask = 1;
    if((n & binMask) == 0) {
        System.out.print("this number is even");
    } else {
        System.out.print("this number is odd");
    }
}

// Get ith bit
public static int getIthBit(int n, int i) {
    int bitMask = 1 << i;
    if((n & bitMask) == 0) {
        return 0;
    }
    return 1;
}

// Set ith bit
public static int setIthBit(int n, int i) {
    int bitMask = 1 << i;
    return n | bitMask;
}

// Clear ith bit
public static int clearBit(int n, int i) {
    int bitMask = ~(1 << i);
    return n & bitMask;
}
```

---

## 🚀 Main Method Examples

The main method contains commented examples showing how to use each function. Uncomment the specific sections to test different algorithms:

```java
public static void main(String args[]){
    // Basic function examples
    // PrintHelloworld();
    // calculateSun();
    
    // Array examples
    // int numbers[] = {2, 4, 6, 8, 10, 12, 14, 16};
    // System.out.println("largest value: " + getlargest(numbers));
    // reverse(numbers);
    
    // Searching examples
    // int index = linearSearch(numbers, 10);
    // int index = BinearySearch(numbers, 12);
    
    // Sorting examples
    // BubbleSorting(numbers);
    // Arrays.sort(numbers);
    
    // String examples
    // System.out.println(palindrome("racecar"));
    
    // Bit manipulation examples
    // System.out.println(getIthBit(10, 3));
    // System.out.println(setIthBit(10, 2));
}
```

---

## 📊 Complexity Analysis

| Algorithm | Time Complexity | Space Complexity |
|-----------|----------------|------------------|
| Algorithm | Time Complexity | Space Complexity |
|-----------|----------------|------------------|
| Linear Search | O(n) | O(1) |
| Binary Search | O(log n) | O(1) |
| Bubble Sort | O(n²) | O(1) |
| Selection Sort | O(n²) | O(1) |
| Insertion Sort | O(n²) | O(1) |
| Counting Sort | O(n + k) | O(k) |
| Kadane's Algorithm | O(n) | O(1) |

---

## 📄 License

This is a reference guide for educational purposes.

## 🤝 Contributing

Feel free to contribute by adding more algorithms or improving existing implementations!

---

**Happy Coding! 🚀**