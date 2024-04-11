## 一、函数

1. 两整数之和

   ```c
   //给你两个整数 a 和 b ，不使用 运算符 + 和 -，计算并返回两整数之和。
   int getSum(int a, int b){
       int sum, carry;
       sum = (unsigned int)(a ^ b);
       carry = (unsigned int)(a&b) << 1;
       
       if (carry != 0){
           return getSum(sum, carry);
       }
       return sum;
   }
   
   int getSum(int a, int b){
       if(b == 0){
           return a;
       }
       return add(a^b, (unsigned int)(a&b) << 1);
   }
   ```

2. 不用加号的加法

   ```c
   //设计一个函数把两个数字相加。不得使用 + 或者其他算术运算符。
   int add(int a, int b){
   	if(b == 0){
           return a;
       }
       return add(a^b, (unsigned int)(a&b) << 1);
   }
   ```

3. 不用加减乘除做加法

   ```c
   /*
   计算机安全专家正在开发一款高度安全的加密通信软件，需要在进行数据传输时对数据进行加密和解密操作。假定 dataA 和 dataB 分别为随机抽样的两次通信的数据量：
   
   正数为发送量
   负数为接受量
   0 为数据遗失
   请不使用四则运算符的情况下实现一个函数计算两次通信的数据量之和（三种情况均需被统计），以确保在数据传输过程中的高安全性和保密性。
   示例 1:
   
   输入：dataA = 5, dataB = -1
   输出：4
    
   
   提示：
   
   dataA 和 dataB 均可能是负数或 0
   结果不会溢出 32 位整数
   */
   int encryptionCalculate(int dataA, int dataB){
       int sum, carry;
       if(dataB == 0){
           return dataA;
       }
       sum = dataA ^ dataB;
       carry = (unsigned int)(dataA & dataB) << 1;
   
       if(carry != 0){
           return encryptionCalculate(sum, carry);
       }
   
       return sum;
   }
   ```

4. 递归乘法

   ```c
   /*
   递归乘法。 写一个递归函数，不使用 * 运算符， 实现两个正整数的相乘。可以使用加号、减号、位移，但要吝啬一些。
   
   示例1:
   
    输入：A = 1, B = 10
    输出：10
   示例2:
   
    输入：A = 3, B = 4
    输出：12
   提示:
   
   保证乘法范围不会溢出
   
   利用：AB = A+A(B-1)
   */
   
   #define Max(a, b) a>b ? a:b
   #define Min(a, b) a<b ? a:b
   int multiply(int A, int B){
       int max = Max(A, B);
       int min = Min(A, B);
       
       if(A == 1 || b == 1){
           return A+B-1;
       }
       
       return max+multiply(max, min-1);
   }
   ```

5. 两数相除

   ```c
   /*
   给你两个整数，被除数 dividend 和除数 divisor。将两数相除，要求 不使用 乘法、除法和取余运算。
   
   整数除法应该向零截断，也就是截去（truncate）其小数部分。例如，8.345 将被截断为 8 ，-2.7335 将被截断至 -2 。
   
   返回被除数 dividend 除以除数 divisor 得到的 商 。
   
   注意：假设我们的环境只能存储 32 位 有符号整数，其数值范围是 [−231,  231 − 1] 。本题中，如果商 严格大于 231 − 1 ，则返回 231 − 1 ；如果商 严格小于 -231 ，则返回 -231 。
   */
   ```

6. Pow(x, n)

   ```c
   /*
   实现 pow(x, n) ，即计算 x 的整数 n 次幂函数（即，xn ）。
   */
   double myPow(double x, int n){
       double y;
       int i = n;
       if(n == 0 || x == 1){
           return 1;
       }
       while (n != 0){
           if (n == 1 || n == -1){
               break;
           }
           if(n%2 != 0)
               y*=x;
           x*=x;
           n/=2;
       }
       return i<0 ? 1/(x*y):(x*y);
   }
   ```

7. Sqrt(x)

   ```c
   /*
   给你一个非负整数 x ，计算并返回 x 的 算术平方根 。
   
   由于返回类型是整数，结果只保留 整数部分 ，小数部分将被 舍去 。
   
   注意：不允许使用任何内置指数函数和算符，例如 pow(x, 0.5) 或者 x ** 0.5 。
   
   目前仅使用内部函数处理
   */
   int mySqrt(int x){
       return (int)sqrt(x);
   }
   ```

8. 最值函数

   ```c
   /*
   面试题 16.07. 最大数值
   编写一个方法，找出两个数字a和b中最大的那一个。不得使用if-else或其他比较运算符。
   */
   int maximun(int a, int b){
       return a > b ? a : b;
   }
   ```

### 二、循环

1. 设计机械累加器

   ```c
   /*
   请设计一个机械累加器，计算从 1、2... 一直累加到目标数值 target 的总和。注意这是一个只能进行加法操作的程序，不具备乘除、if-else、switch-case、for 循环、while 循环，及条件判断语句等高级功能。
   
   目前可以先使用循环
   */
   int mechanicalAccumulator(int target){
       int sum = 0;
       if (target < 0 || target == 0)
           return -1;
       for(int i = 0; i <= target; ++i)
           sum+=i;
       return sum;
   }
   ```

2. 2的幂

   ```c
   /*
   给你一个整数 n，请你判断该整数是否是 2 的幂次方。如果是，返回 true ；否则，返回 false 。
   
   如果存在一个整数 x 使得 n == 2x ，则认为 n 是 2 的幂次方。
   
   */
   bool isPowerOfTwo(int n){
       unsigned int k = 1;
       int i;
       if (n == 1)
           return true;
       if (n <= 0)
           return false;
       for (i = 0; i <= 31; ++i){
           k*=2;
           if (k == n)
               return true;
       }
       return false;
   }
   ```

3. 3的幂

   ```c
   /*
   3 的幂
   
   给定一个整数，写一个函数来判断它是否是 3 的幂次方。如果是，返回 true ；否则，返回 false 。
   
   整数 n 是 3 的幂次方需满足：存在整数 x 使得 n == 3x
   
   */
   bool isPowerOfThree(int n){
       unsigned int k = 1;
       if (n = 1)
           return true;
       if (n <= 0)
           return false;
       for(int i = 0; i <= 20; ++i){
           k*=3;
           if(k == n)
               return true;
       }
       return false;
   }
   ```

4. 4的幂

   ```c
   /*
   4的幂
   给定一个整数，写一个函数来判断它是否是 4 的幂次方。如果是，返回 true ；否则，返回 false 。
   
   整数 n 是 4 的幂次方需满足：存在整数 x 使得 n == 4x
   */
   bool isPowerOfFour(int n) {
       unsigned int k = 1;
       if(n <= 0)
           return false;
       if(n == 1)
           return true;
       for(int i = 0; i <= 15; ++i){
           k*=4;
           if(k == n){
               return true;
           }
       }
       return false;
   }
   ```

   