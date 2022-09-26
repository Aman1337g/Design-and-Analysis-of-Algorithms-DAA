# 1. Introduction to Algorithms

It is a step by step procedure to solve a computational problem.<br>
Now what is a program??<br>
It is also a step by step procedure to solve a computational problem.<br>

**Difference between Algorithm and Program**

| Algorithm | Program |
|-----------|-----------|
| Written at design time.          | Written at implementation time.          |
| Person who should write an algorithm should have domain knowledge of the problem. | Programmer will write the program. |
| Any language (English , mathematical notation) can be used to write an algorithm. | Only written using programming language (like C , C++ , Java , Python etc). |
| Hardware and Operating System independent. | Hardware and Hardware and Operating System dependent. |
| We analyze an algorithm. | We test a program. |

<br>

## 1.1 Priori Analysis and Posteriori Testing

| Priori Analysis | Posteriori Testing |
|---|---|
| Done for Algorithm | Done for a program |
| Independent of language | Language dependent |
| Hardware independent | Hardware dependent |
| We get time and space **function** | We watch time and bytes consumed |

<br>

## 1.2 Characteristics of Algorithm 

1. Input - takes 0 or more inputs.
2. Output - must generate atleast one output otherwise of no use.
3. Definiteness - every statement must be clear. (eg - root(-1) cannot be read as real number).
4. Finiteness - duration of algorithm must be finite.
5. Effectiveness - should not have any unnecessary statements.

<br>

## 1.3 How to Analyze an Algorithm

An algorithm can be anlyzed on the basis of -
1. Time - we get a time **function**.
2. Space - memory space consumption.
3. Network consumption - Nowadays , every application is either internet based , web based or cloud based so data transfer or network consumption is also an important criteria.
4. Power consumption
5. CPU registers - if developing programs for device drivers or system level programming then we also need to know how much CPU registers it is consuming

Consider an algorithm -
```
Algorithm Swap(a, b)
{
    temp = a;     <------ 1 unit time
    a = b;        <------ 1    "
    b = temp;     <------ 1    "
}
```
1. Time Analysis - Generally , we take every statement is consuming 1 unit of time.<br>
So , time taken = f(n) = 3 (constant) OR Order of 1 = O(1)

2. Space Analysis - parameter used = a, b and local variable = temp<br>
So , S(n) = 1+1+1 = 3 words (constant) OR Order of 1 = O(1)

<br>

## 1.4 Frequency Count Method

Consider an algorithm -
```
Algorithm sum(A, n)
{
    s = 0;                 <---- 1 unit time
    for(i=0 ; i<n; i++)    <---- n+1 unit time
    {
        s = s + A[i];      <---- n unit time
    }
    return s;              <---- 1 unit time
}
```

1. Time Analysis - 'i' is incrementing 'n' times but the comparision is done for 'n+1' times ( i=0, i=1, i=2, .... i=n ) and i=0(Assignment) takes 1(constant) time<br>
We consider only time taken in comparision so 'n+1'<br>
Total time taken = 1 + (n+1) + n + 1 = 2n+3.<br>
Degree of this polynomial = 1 OR order of n = O(n)

2. Space Analysis - Variable used are A, n, s, i and size of A is n words.<br>
So , space consumed = n+1+1+1 = n+3 words OR order of n = O(n)

Consider an another algorithm -
```
Algorithm add(A, B, n) 
{
    for(i=0; i<n; i++)                  <------ (n+1) unit time
    {
        for(j=0; j<n; j++)              <------ n*(n+1) unit time
        {
            C[i,j] = A[i,j] + B[i,j];   <------ n*n unit time
        }
    }
}
```

1. Time Analysis - f(n) = (n+1) + n*(n+1) + n*(n) = 2*(n)^2 + 2*n + 1 OR O(n^2)

2. Space Analysis - 

    | Variables | Size |
    |---|---|
    | A | n^2 words |
    | B | n^2 words |
    | C | n^2 words |
    | n | 1 word |
    | i | 1 word |
    | j | 1 word |

    So , S(n) = 3*(n)^2 + 3 OR O(n^2)

Consider another algorithm -
```
Algorithm multiply(A, B, n) 
{
    for(i=0; i<n; i++)                             <------ (n+1) unit time
    {
        for(j=0; j<n; j++)                         <------ n*(n+1) unit time
        {
            C[i,j] = 0;                            <------ n*(n) unit time
            for(k=0; k<n; k++)                     <------ n*n*(n+1) unit time
            {
                C[i,j] = C[i,j] + A[i,k]*B[k,j];   <------ n*(n)*(n) unit time
            }
        }
    }
}
```

1. Time Analysis - f(n) = (n+1) + (n * (n+1)) + (n * n) + (n * (n) * (n+1)) + (n * n * n) = 2*(n)^3 + 3*(n)^2 + 2*n + 1 OR O(n^3)

2. Space Analysis - 

    | Variables | Size |
    |---|---|
    | A | n^2 words |
    | B | n^2 words |
    | C | n^2 words |
    | n | 1 word |
    | i | 1 word |
    | j | 1 word |
    | k | 1 word |

    So , S(n) = 3*(n)^2 + 4 OR O(n^2)

<br>

## 1.5.1 Time Complexity #1

1. a)
```
for(i=0; i<n; i++) {
    // statements;      <--- n unit time
}
```
So, Time Complexity = Order of n = ```O(n)```
    
b)
```
for(i=n; i<0; i--) {
    // statements;      <--- n unit time
}
```
So, Time Complexity = Order of n = ```O(n)```

2. a)
```
for(i=1; i<n; i+2) {
    // statements;      <--- n/2 unit time
}
```
So, Time Complexity = Order of n/2 = ```O(n)```

b)
```
for(i=1; i<n; i+a) {    // Where a = positive number
    // statements;      <--- n/a unit time
}
```
So, Time Complexity = Order of n/a = ```O(n)```

3. a)     

```
for(i=0; i<n; i++)                             <--- (n+1) unit time
{
    for(j=0; j<n; j++)                         <--- n*(n+1) unit time
    {
        // statements;                         <--- n*n unit time
    }
}
```
So, Time Complexity = Order of n^2 = ```O(n^2)```

b)   

```
for(i=0; i<n; i++)                             
{
    for(j=0; j<i; j++)                         
    {
        // statements;                         
    }
}
```

### **Tracing this code :**

| i | j | No. of times run |
|---|---|---|
| 0 | 0(x) | 0 |
| 1 | 0, 1(x) | 1 |
| 2 | 0, 1, 2(x) | 2 |
| 3 | 0, 1, 2, 3(x) | 3 |

This will continue till i = n, j = 0, 1, 2, 3, 4, .... , n-1

So, Time Complexity = f(n) = 0 + 1 + 2 + 3 + ... + n = (n*(n+1))/2 . So , order of n^2 = ```O(n^2)```.

4. a)     

```
p=0;
for(i=1; p<=n; i++)     <--- (n+1) unit time
{
    p = p + i;
}
```
### **Tracing this code :**

| i | p | No. of times run |
|---|---|---|
| 1 | 0+1=1 | 1 |
| 2 | 1+2=3 | 2 |
| 3 | 1+2+3 | 3 |
| 4 | 1+2+3+4 | 3 |

Let it runs 'k' times such that 'p' becomes > n ,<br>
so  (k*(k+1))/2 > n<br>
=> k^2>n<br>
=> k>root(n)<br>
So, Time Complexity = Order of n^(1/2) = ```O(root(n))```

***Main idea is to find to number of times the code will run till terminating condition is reached***

<br>

## 1.5.2 Time Complexity #2

5.
```
for(i=1; i<n; i=i*2) {
    // statements;
}
```
### **Tracing this code :**

| i |
|---|
| 1 |
| 2*2 |
| (2^2)*2 |
| (2^3)*2 |

Let this continues for k times such that 'i' becomes greater than or equal to n<br>
=> i>=n<br>
=> 2^k >= n<br>
=> k = log(n) on base 2

So, Time Complexity = Order of log(n) = O(log(n)) OR = ```O(ceil(log(n)))```

OR, we can look it as i = 1x2x2x2x2x.....x till 'k' times when i >= n => 2^k = n or ```k = log(n) on base 2```

6.
```
for(i=n; i>=1; i=i/2) {
    // statements;
}
```
### **Tracing this code :**

| i |
|---|
| n |
| n/2 |
| (n/2)/2 |
| (n/(2^2))/2 |

Let this continues for k times such that 'i' becomes less than 1<br>
=> i<1<br>
=> n/(2^k) < 1<br>
=> k = log(n) on base 2

So, Time Complexity = Order of log(n) = O(log(n)) OR = ```O(ceil(log(n)))```

OR, we can look it as i = n/2/2/2/2/...../ till 'k' times when i < 1 => n/(2^k) = 1 or ```k = log(n) on base 2```

7.    

```
for(i=1; i*i<n; i++)                             
{
    // statements;      
}
```
Now, this code will run until i*i >= n<br>
=> 'i' becomes root(n)<br>
So, Time Complexity = Order of n^(1/2) = ```O(root(n))```

8.     
```
for(i=0; i<n; i++)
{
    // statements;      <--- n unit time
}
for(j=0; j<n; j++)      
{
    // statements;      <--- n unit time
}
```
So, Time Complexity = Order of (n+n) = O(2n) = ```O(n)```

9.     
```
p=0;
for(i=1; i<n; i=i*2)
{
    p++;      <--- log(n) unit time , so p will become log(n)
}
for(j=1; j<p; j=j*2)      
{
    // statements;      <--- log(p) unit time
}
```
So, Time Complexity = Order of log(p) = ```O(log(log(n)))``` [As p = log(n)]

9.     
```
for(i=1; i<n; i=i++)        <--- n unit time [you can take it 'n' instead of 'n+1']
{
    for(j=1; j<n; j=j*2)    <--- n*log(n) unit time
    {
        // statements;      <--- n*log(n) unit time
    }
}
```
So, Time Complexity = Order of (2n*log(n) + n) = ```O(n(log(n)))```

**Cases we have disscused so far :**

| Case | Time Complexity |
|---|---|
| for(i=0; i<n; i++) | O(n) |
| for(i=0; i<n; i=i+2) | O(n/2) = O(n) |
| for(i=n; i>1; i--) | O(n) |
| for(i=1; i<n; i=i*2) | O(log(n)) , base = 2 |
| for(i=1; i<n; i=i*3) | O(log(n)) , base = 3 |
| for(i=n; i>1; i=i/2) | O(log(n)) , base = 2 |
