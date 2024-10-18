# Bit Manipulation in Java 🔢

Bit manipulation is a powerful tool in programming, often used to optimize space and performance by performing operations directly on binary digits. In this guide, we will explore common bit manipulation operations: setting a bit, clearing a bit, checking a bit, XOR operations, and some sample problems to practice.

---

## 📖 Table of Contents
- [Introduction](#introduction)
- [Bit Representation](#bit-representation)
- [Setting a Bit](#setting-a-bit)
- [Clearing a Bit](#clearing-a-bit)
- [Checking a Bit](#checking-a-bit)
- [XOR Operation](#xor-operation)
- [Sample Problems](#sample-problems)
- [Conclusion](#conclusion)

---

## 📝 Introduction

In computers, data is stored in binary format (0s and 1s). By using bitwise operations, we can manipulate data at the bit level, allowing for more efficient computation in scenarios like toggling flags, optimizing space, or implementing algorithms.

---

## 🧠 Bit Representation

Each bit in a number can be represented by a power of two, from right to left starting at 0:
```
Binary Representation:   1011 (binary for 11)
Bit Positions:           3210  (positions from right to left)
```

The following operations will allow us to manipulate specific bits in a number.

---

## ⚙️ Setting a Bit

To set a specific bit to 1 (turn it ON), we use the **bitwise OR** (`|`) operator along with a bitmask. A bitmask is a number where only the bit we want to set is 1, and the rest are 0.

### Formula:
```java
number |= (1 << i);
```

### Example:
Set the 2nd bit (position 1) in the number 5 (binary `0101`):

```java
int number = 5; // 0101
int i = 1;
number |= (1 << i); // 0111 -> 7 in decimal
System.out.println(number); // Output: 7
```

---

## 🛠 Clearing a Bit

To clear a specific bit to 0 (turn it OFF), we use the **bitwise AND** (`&`) operator combined with a NOT (`~`) operator.

### Formula:
```java
number &= ~(1 << i);
```

### Example:
Clear the 2nd bit (position 1) in the number 7 (binary `0111`):

```java
int number = 7; // 0111
int i = 1;
number &= ~(1 << i); // 0101 -> 5 in decimal
System.out.println(number); // Output: 5
```

---

## 🔍 Checking a Bit

To check whether a bit at position `i` is set to 1 or 0, we use the **bitwise AND** (`&`) operator and check if the result is non-zero.

### Formula:
```java
boolean isSet = (number & (1 << i)) != 0;
```

### Example:
Check if the 3rd bit (position 2) in the number 5 (binary `0101`) is set:

```java
int number = 5; // 0101
int i = 2;
boolean isSet = (number & (1 << i)) != 0;
System.out.println(isSet); // Output: true
```

---

## 🔄 XOR Operation

The XOR operation (`^`) is useful for toggling (flipping) bits. It sets the bit to 1 if the bits are different and 0 if the bits are the same.

### Formula:
```java
number ^= (1 << i);
```

### Example:
Toggle the 3rd bit (position 2) in the number 5 (binary `0101`):

```java
int number = 5; // 0101
int i = 2;
number ^= (1 << i); // 0001 -> 1 in decimal
System.out.println(number); // Output: 1
```

---

## 🎯 Sample Problems

### Problem 1: Count the Number of Set Bits

Write a Java function that returns the number of 1s (set bits) in the binary representation of a given integer.

#### Solution:
```java
public class BitManipulation {
    public static int countSetBits(int number) {
        int count = 0;
        while (number > 0) {
            count += (number & 1); // Check the last bit
            number >>= 1;          // Right shift to process the next bit
        }
        return count;
    }

    public static void main(String[] args) {
        int number = 29; // Binary: 11101
        System.out.println(countSetBits(number)); // Output: 4
    }
}
```

### Problem 2: Check if a Number is a Power of Two

Write a function to check if a number is a power of two using bit manipulation.

#### Solution:
```java
public class BitManipulation {
    public static boolean isPowerOfTwo(int number) {
        return (number > 0) && (number & (number - 1)) == 0;
    }

    public static void main(String[] args) {
        int number = 16;
        System.out.println(isPowerOfTwo(number)); // Output: true
    }
}
```

### Problem 3: Swap Two Numbers Without Using a Temporary Variable

Swap two integers using XOR.

#### Solution:
```java
public class BitManipulation {
    public static void swap(int a, int b) {
        a = a ^ b;
        b = a ^ b;
        a = a ^ b;
        System.out.println("After swapping: a = " + a + ", b = " + b);
    }

    public static void main(String[] args) {
        int a = 5, b = 9;
        System.out.println("Before swapping: a = " + a + ", b = " + b);
        swap(a, b);
    }
}
```

---

## 🔚 Conclusion

Bit manipulation can significantly improve the efficiency of your code, especially when working with low-level programming tasks. Mastering these operations will help you solve many competitive programming and interview questions. Keep practicing to get comfortable with bitwise operations!
