# C-Program-to-Check-Whether-a-Number-is-Palindrome-or-Not

Palindrome Number in C
Via this article, we will learn how to check if a number is palindrome or not using c programming language. We will look at different ways to check Palindrome Number in C.

A palindrome number is a number that is given the same number after reverse. 

Example:-

A number is 123321. If you read number “123321” from reverse order, it is same as “123321”. 
A number is 12121. If we read number “12121” from reverse order ,it is same as 12121. It is also a palindrome number 
palindrome or not in c
Methods Discussed
Method 1: Basic Mathematical Approach
Method 2: Recursive Approach
Other methods

Method 3: String approach using for loop
Method 4: String approach using updated for loop
Method 5: String approach using Binary search style while loop
Method 1:
Working for Palindrome Program in C

For an input num

Take user input in num
Find the reverse value of num in another variable ‘rev‘
Check if rev == num
Palindrome or not in C
While loop in C
Method 1
Run

// Palindrome program in C
#include<stdio.h> 

// Palindrome is a number that is same if read forward/backward
// Ex : 12321
int main ()
{
    int num, reverse = 0, rem, temp;
    num=11211;
    printf("The number is :%d\n",num);
 
    temp = num;
    
    //loop to find reverse number
    while(temp != 0)
    {
        rem = temp % 10;
        reverse = reverse * 10 + rem;
        temp /= 10;
    };
    
    // palindrome if num and reverse are equal
    if (num == reverse)
        printf("%d is Palindrome\n", num);
    else
        printf("%d is Not Palindrome\n", num);

}
// Time Complexity : O(N)
// Space Complexity : O(1)
// Where N is number of digits in num
Output:-
The number is: 11211
11211 is Palindrome
Method 2 (Recursive Approach)
This method uses recursion in C

Run

#include<stdio.h> 

// Recursive way to find reverse of a number
int getReverse(int num, int rev){
    if(num == 0)
        return rev;
    
    int rem = num % 10;
    rev = rev * 10 + rem;
    
    return getReverse(num / 10, rev);
}

int main ()
{
    int num, reverse = 0;
    num=12321;
    printf("The number is: %d\n",num);
        
    // palindrome if num and reverse are equal
    if (num == getReverse(num, reverse))
        printf("%d is Palindrome\n", num);
    else
        printf("%d is Not Palindrome\n", num);

}
// Time Complexity : O(N)
// Space Complexity : O(1)
// Auxilary Space Complexity : O(N)
// Where N are number of digits in a number
Output:-
The number is: 12321
12321 is Palindrome
Related Pages
Program to find Sum of digits of number

Program to reverse a number

Program to check armstrong number

Armstrong number in a given range

Fibonacci series up to n numbers

Other Methods
The below method will work if we have a string input

Method 3
Palindrome Program in C

For a String of Length: Len
Run an iterative loop in an iteration of i
If encounter any index such that arr[i] != arr[len – i -1], then the string is not palindrome
Otherwise if no condition such found in whole iteration in loop then string is palindrome
Run
#include <stdio.h>
#include <string.h>

int main() 
{
    char str[10] = "naman";
    int i, len, flag = 0;
    
    len = strlen(str);

    for (i = 0; i < len; i++) 
    {
        // Checking if string is palindrome or not
        if (str[i] != str[len - i - 1]) {
            flag = 1;
            break;
        }
    }

    if (flag)
        printf("%s is not palindrome", str);
    else
        printf("%s is palindrome", str);
        
    return 0;
}
Output
naman is palindrome
While loop in C
Method 4
This method is same as the above method with two minor differences –

Difference 1
For loop runs only till len/2 not the whole length of the string
Since the other half, the string will be the same as the first half. If the string is a palindrome
Difference 2
We also handle capitalization
The previous method would have said “Naman” is not palindrome as N is not equal to n
This method converts whole string into lowercase and thus will say that “Naman” is palindrom
Run
#include <stdio.h>
#include <string.h>

void lowerCase(char str[]){
  int i = 0;
  while (str[i] != '\0')
  {
    if (str[i] > 64 && str[i] < 91) 
      str[i] += 32; 
    i++;
  }
}
int main() 
{
    char str[10] = "Naman";
    int i, len, flag = 0;
    
    lowerCase(str);
    
    len = strlen(str);
    
    // only need to check till half of the array
    for (i = 0; i < len / 2; i++) 
    {
        // Checking if string is palindrome or not.
        if (str[i] != str[len - i - 1]){
            flag++;
            break;
        }
    }

    if (flag)
        printf("String is not palindrome");
    else
        printf("String is palindrome");
        
    return 0;
}
Output
String is palindrome
Method 5
This method is the same as the above method. However, instead of for loop, we use a whole loop.

The approach is very similar to Binary search looping

Run
#include <stdio.h>
#include <string.h>


void Lower_case(char str[]) {
    int i = 0;
    while (str[i] != '\0') {
        if (str[i] > 64 && str[i] < 91) str[i] += 32;
        i++;
    }
}

void CheckPalindrome(char str[]) 
{
    // to mark left most and right most indexes of string
    int left = 0;
    int right = strlen(str) - 1;
    
    // Keep comparing characters while they are same
    // until left and right overlap one another
    // inspiration for this approach taken from binary search
    while (right > left) 
    {
        if (str[left++] != str[right--]) {
            printf("The String %s is not a palindrome", str);
            return;
        }
    }
    printf("The String %s is palindrome", str);
}
int main() 
{
    char str1[50] = "Radar";
    
    Lower_case(str1);
    CheckPalindrome(str1);
    
    return 0;
}
Output
The String radar is palindrome
