# Ways to find the leading zeros of a number in its binary form

## Using the inbuilt cpp function
```
int n = 4
int zeros = __builtin_clz(n)
cout << zeros << endl;
```

Output:
```
29
```
> Note that the binary form of the number will be presented in the 32 bit format



## Checking the highest power of 2 of the number 
```
int zeros = 0;
while((1 << (zeros+1))<= n){
  ++zeros;
}
cout << zeros << endl;
```
Output
```
2
```
> Note that the binary form of the number will be presented in the 4 bit format

