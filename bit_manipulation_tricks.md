# Bit Manipulation Tricks

### Check if the bit is even or odd
```
bool isEven(int n) return (n&1)==0;

```

### Swap 2 numbers without a temporary variable
```
void swap(int a, int b){
  a = a^b;
  b = a^b;  
  a = a^b;
}
```

### Multiply and divide by 2 using Bitwise Shifts
```
int MultiplyBy2(int n) return n << 1;
int DivideBy2(int n) return n >> 1;
```

### Check if number is power of 2
```
bool isPowerOf2(int n) return (n>0) && (n&(n-1)) == 0;

```

### Count the number of set bits (Hamming Distance)
```
int countSetBits(int n){
  int count = 0;
  while(n){ count += n&1; n>>=1;} return count;}
```

### Clear the LSB
```
int clearLSB(int n) return n & (n-1);

```

### Get the LSB
```
int getLSB(int n) return n & -n;

```

### Set a specific bit
```
int setBit(int n, int k) return n | (1<<k);

```

### Clear a specific bit
```
int clearBit(int n, int k) return n & ~(1<<k);

```

### Flip all bits
```
int flipBits(int n) return ~n;

```

### Check if specific bit is set
```
bool isBitSet(int n, int k) return (n & ( 1<< k)) != 0;

```

### Toggle a specific bit
```
int ToggleBit(int n, int k) return n ^ (1<<k);

```

