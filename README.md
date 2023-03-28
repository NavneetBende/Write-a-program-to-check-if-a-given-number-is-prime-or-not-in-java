# Write-a-program-to-check-if-a-given-number-is-prime-or-not-in-java

Given an integer input, the objective is to – Write a program to check if a given number is prime or not in Java. Here are some of the Methods to Check for Prime –

Method 1: Simple iterative solution
Method 2: Optimization by break condition
Method 3: Optimization by n/2 iterations
Method 4: Optimization by √n
Method 5: Optimization by skipping even iteration
Method 6: Basic Recursion technique
We’ll discuss the above-mentioned methods in detail in the sections below. Check out the Blue box mentioned below to know more about prime numbers.

Prime No Program in Java
Prime Number
A prime number is a natural number greater than 1 that is not a product of two smaller natural numbers. A natural number greater than 1 that is not prime is called a composite number. For example, 5 is prime because the only ways of writing it as a product, 1 × 5 or 5 × 1, involve 5 itself.
Method 1: Simple iterative solution
Working
In this method, we’ll iterate through all the numbers that lay in the interval [1, number] and check if any of them is a factor of the number, if so it’s not a Prime.

For a given integer input we check for the following,

If the count of factors for this number is > 2 then
It’s not prime else it’s prime
A prime number must only be divisible by 1 and the number itself.
Java Code
Run
// Time Complexity : O(N)
// Space Complexity : O(1)
public class Main
{
    public static void main (String[]args)
    {
        int n = 23;
        checkPrime(n);
    }

    private static void checkPrime(int n) {
        int count = 0;

        // negative numbers, 0 and 1 are not prime
        if (n < 2)
            System.out.println ("The given is number " + n + " is not prime");

        // checking the number of divisors b/w [1, n]
        for (int i = 1; i <= n; i++) 
        { 
            if (n % i == 0) 
                count += 1; 
        } 

        // if count of divisors greater than 2 then its not prime 
        if (count > 2)
            System.out.println ("The given is number " + n + " is not prime");

        else
            System.out.println ("The given is number " + n + " is prime");
    }
}
Output
23 is : Prime
Related Pages
Greatest of the Three numbers

Leap year or not

Prime number within a given range

Sum of digits of a number

Reverse of a number

Method 2: Optimization by break condition
Working
In the above mentioned we’ll divide the whole loop situation into two parts, we’ll check if the number is lesser than 2, it’s not a prime. It also mustn’t have factors between range [2, num-1]

For an integer input, we check the following,

If the number is lesser than 2.
If the number has any factors other than 1 and itself.
If either of the above two conditions are satisfied, the number is not a Prime.
Java Code
Run

// Write a java program to check whether a given number is prime or not
public class Main
 {
   public static void main (String[]args)
   {

     int i, n = 13;
     boolean isprime = true;

     // 0 and 1 are not prime numbers also, negative numbers are not prime
     if (n < 2)
       {
          isprime = false;
       }
     else
       {
          for (i = 2; i < n; i++)
           {
            if (n % i == 0)
             {
              isprime = false;
                  break;
                }
        }
       }

     String result = isprime ? "Prime" : "not Prime";
     System.out.println ("The number " + n + " is : " + result);

     // Time Complexity : O(N)
     // Space Complexity : O(1)
     // This program is better than previous version as :
     // Condition for 0, 1 and negative numbers checked earlier
     // Loops runs b/w [2, n-1] rather than [1, n]

   }
 }
Output
 13 is : Prime
Method 3: Optimization by n/2 iterations
Working
In this method, we’ll only run the loop until number/2.

As it’s known that the smallest factor of every number if any, will lie in the interval [2, number/2].

For an integer input, we do the following –

Check if the number is lesser than 2.
Check if the number has any factors other than 1 and the number itself in the interval [2, number/2].
If either if the conditions are satisfied, the number is not a Prime.
Java Code
Run
// Prime no Program in Java
public class Main
 {
   public static void main (String[]args)
   {

     int i,n = 33;
     boolean isprime= true;

     // 0 and 1 are not prime numbers also, negative numbers are not prime
     if(n < 2)
     {
         isprime = false;
     }
     else
     {
     // running loop till n is wasteful because for any number n the numbers in
     // the range(n/2 + 1, n) won't be divisible anyways.
         for(i=2; i <= n/2; i++)
         {
             if(n % i == 0)
             {
                 isprime = false;
                 break;
             }
         }
     }

     String result = isprime ? "Prime" : "not Prime";
     System.out.println ("The number " + n + " is : " + result);

     // Time Complexity : O(N)
     // Space Complexity : O(1)
     // This program is better than previous version as :
     // Loops runs b/w [2, n/2] rather than [2, n-1]


   }
 }
Output
 33 is : Not Prime
Method 4: Optimization by √n
Working
In this method we’ll use for loop to iterate from 2  to square root of the number as it’s known that all the factors of the number lay in the interval [2, sqrt(number)].

For an integer input number, we check,

If the number is lesser than 2.
If the number has factors other than 1 and the number itself in the interval [2, sqrt(number)].
If either of the conditions are satisfied, the number is not a Prime.
Java Code
Run
public class Main
 {
   public static void main (String[]args)
   {

      int i,n = 29;
     boolean isprime= true;

     // 0 and 1 are not prime numbers also, negative numbers are not prime
     if(n < 2)
     {
         isprime = false;
     }
     else
     {
     // If a number n is not a prime, it can be factored into two factors a and b:
     // n = a * b

     /*Now a and b can't be both greater than the square root of n, 
     since then the product a * b would be greater than sqrt(n) * sqrt(n) = n.
     So in any factorization of n, at least one of the factors must be smaller 
     than the square root of n, and if we can't find any factors less than or equal to 
     the square root, n must be a prime.*/
         for(i=2; i <= Math.sqrt(n); i++)
         {
             if(n % i == 0)
             {
                 isprime = false;
                 break;
             }
         }
     }

     String result = isprime ? "Prime" : "not Prime";
     System.out.println ("The number " + n + " is : " + result);

     // Time Complexity : O(N)
     // Space Complexity : O(1)
     // This program is better than previous version as :
     // Loops runs b/w [2, bn] rather than [2, n/2]


   }
 }
Output
29 is : Prime
Method 5: Optimization by skipping even iteration
Working
In this method we’ll use the for loop to iterate through the number in the given range [3, sqrt(number)] with a step of +1. We all know that an even number can’t be a prime and the only even prime is 2. Therefore we’ll run the loop with step 1 which will skip all the even numbers.

For a given integer input we check,

If the number is lesser than 2.
If the number has any factors other than 1 and the number itself in the given range of [3, sqrt(number)].
We skip one iteration until the last element in reached.
If either of the above conditions are satisfied, then the number is not a Prime.
Java Code
Run
public class Main
 {
   public static void main (String[]args)
   {

     int n = 29;

     if (isPrime (n))
         System.out.println (n + " is a Prime Number");
     else
         System.out.println (n + " is not a Prime Number");

   }


   static Boolean isPrime (int n)
   {
     // 0 and 1 are not prime numbers
     // negative numbers are not prime
     if (n <= 1)
       return false;

     // special case as 2 is the only even number that is prime
     else if (n == 2)
       return true;

     // Check if n is a multiple of 2 thus all these won't be prime
     else if (n % 2 == 0)
       return false;

     // If not, then just check the odds
     for (int i = 3; i <= Math.sqrt (n); i += 2)
       {
 	if (n % i == 0)
 	  return false;
       }

     return true;
   }
 }
Output
29 is : Prime
Method 6: Basic Recursion technique
Working
In this method we’ll use recursion to recursively iterate through each number and check whether it’s a factor of the number of not. To learn more about recursion in java, check out Recursion .

For a given integer input,

Define a recursive function with base case as follows
If number == iter, return True.
If number%iter == 0, return False.
If a number<2, return False.
Set recursive step call as checkPrime(number, iter+1).
Java Code
Run
public class Main
{
  public static void main (String[]args)
  {

    int i = 2;
    boolean isprime= true;
    
    int n = 37;
    isprime=checkPrime(n, i);
    
    String result = isprime ? "Prime":"not Prime";
    System.out.println(n + " is : "+ result); 

  }


  static Boolean checkPrime(int n, int i)
{
    // 0, 1 and negative numbers are not prime
    if (n < 2)
        return false;

    // if this satisfies then its prime as we
    // have completed recursion from 2 to n
    if (i == n)
        return true;

    // Base cases
    if (n % i == 0)
        return false;

    i += 1;
    return checkPrime(n, i);
}
}
Output
37 is : Prime
