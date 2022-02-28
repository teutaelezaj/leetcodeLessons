# Shift Operators

**Left Shift**
```
int a = 8; //1 0 0 0
int b = a << 2; // 1 0 0 0 0 0 -> adds 2 zeros, value is now 32
 
System.out.println(b);
Output = 32
```

**Right Shift**
```
int a = 8; //1 0 0 0
int b = a >> 2; // 1 0 -> removes 2 zeros, value is now 2
 
System.out.println(b);
Output = 2
```
**Changing the value of a**
```
int a = 25; //1 1 0 0 1
int b = a >> 2; // 1 1 0 -> removes the last 2 values, value is now 6
System.out.println(b)
Output = 6
```

