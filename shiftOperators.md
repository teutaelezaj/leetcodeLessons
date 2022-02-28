# Shift Operators

**Left Shift:**
```
int a = 8; //1 0 0 0
int b = a << 2; // 1 0 0 0 0 0 -> adds 2 zeros, value is now 32
 
System.out.println(b);
Output = 32
```

**Right Shift:**
```
int a = 8; //1 0 0 0
int b = a >> 2; // 1 0 -> removes 2 zeros, value is now 2
 
System.out.println(b);
Output = 2
```
**Changing the Value of int a:**
```
int a = 25; //1 1 0 0 1
int b = a >> 2; // 1 1 0 -> removes the last 2 values, value is now 6
System.out.println(b)
Output = 6
```
## Leetcode "Number of 1 Bits"
Write a function that takes an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).

```
Input: n = 00000000000000000000000000001011
Output: 3
Explanation: The input binary string 00000000000000000000000000001011 has a total of three '1' bits.
```

```
Input: n = 00000000000000000000000010000000
Output: 1
Explanation: The input binary string 00000000000000000000000010000000 has a total of one '1' bit.
```

**Solution**
```
public class Solution {
   public int hammingWeight(int n) { 
    int bits = 0; 
    int mask = 1;
    for (int i = 0; i < 32; i++) { //32 bits long
        if ((n & mask) != 0) { 
            bits++; 
        }
        mask <<= 1; 
    }
    return bits;
    }
}
```

We check each of the 32 bits of the number. If the bit is 1, we add one to the number of 1-bits.

We can check the i^th bit of a number using a bit mask. We start with a mask m=1, because the binary representation of 1 is 00000000000000000000000000000001. Clearly, a logical AND between any number and the mask 1 gives us the least significant bit of this number. To check the next bit, we shift the mask to the left by one.

00000000000000000000000000000010
00000000000000000000000000000010

And so on.

**Notes:**
`mask <<= 1` is just shorthand for `mask = mask << 1`

You could also do `return Integer.bitCount(n);` which returns the count of the number of one-bits in the two’s complement binary representation of an int value. 



