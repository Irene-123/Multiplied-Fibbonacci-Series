# Multiplied-Fibbonacci-Series
Multiplication of two successive Fibbonacci Numbers

![image](https://user-images.githubusercontent.com/58950467/87566282-6b191000-c6e0-11ea-9c8f-29ee67a4b4bf.png)



The solution:
 ```
 int fibbo(int n){
   int sum=0;
   if (n==0 || n==1)    //base case
     return 2;
     for (int i=1; i<n;i++)
       sum+=2*fibbo(i) * fibbo(i-1);
     return sum;
   }
  ```
  
  Problem-2 Can we improve the solution to Problem-1 using memoization of DP?
  
  T(0) = T(1) = 2
T(2) = 2 * T(1) * T(0)
T(3) = 2 * T(1) * T(0) + 2 * T(2) * T(1)
T(4) = 2 * T(1) * T(0) + 2 * T(2) * T(1) + 2 * T(3) * T(2)
From the above calculations it is clear that there are lots of repeated calculations with the same
input values. Let us use a table for avoiding these repeated calculations, and the implementation
can be given as:
```
 int fibbo(int n) {
 T[0]=T[1] =2;
 for (int i=2;i<=n;i++) {
     T[i]=0;
     for (int j=1;j<i;j++)
       T[i]+= 2* T[j] * T[j-1];
     }
   return T[n];
 }
 ```
 Time complexity: O(n<sup>2</sup>); for two ```for``` loops .
 Space complexity: O(n)
 
 
 Problem-3 Can we further improve the complexity of Problem-2?
 
 Solution: Yes, since all sub problem calculations are dependent only on previous calculations,
code can be modified as:

```
int fibbo(int n){
 T[0]=T[1]=2;
 T[2]=2*T[0]*T[1];
 for (int i=3;i<=n;i++)
   T[i]= T[i-1]+ 2*T[i-1] *T[i-2];
 return T[n];
}
```
Time complexity: O(n)
 Space complexity: O(n)
