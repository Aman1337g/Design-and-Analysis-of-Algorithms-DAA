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

## 1.1 Priori Analysis and Posteriori Testing

| Priori Analysis | Posteriori Testing |
|---|---|
| Done for Algorithm | Done for a program |
| Independent of language | Language dependent |
| Hardware independent | Hardware dependent |
| We get time and space **function** | We watch time and bytes consumed |

## 1.2 Characteristics of Algorithm 

1. Input - takes 0 or more inputs.
2. Output - must generate atleast one output otherwise of no use.
3. Definiteness - every statement must be clear. (eg - root(-1) cannot be read as real number).
4. Finiteness - duration of algorithm must be finite.
5. Effectiveness - should not have any unnecessary statements.

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