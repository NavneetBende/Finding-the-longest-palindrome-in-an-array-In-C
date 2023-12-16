Longest Palindrome in an Array in C
Here, in this page we will discuss the program to find the longest palindrome in an array in C programming language. We are given with an array and need to print the element of longest length and palindrome in nature.

While loop in C
Method Discussed :
Method 1 : Using Naive Approach
Method 2 : Using Sorting
 
Method 1 :
Create a function ispalindrome(int n), it will return 1 if the passing number is palindrome otherwise return 0.
Inside the main function, create a variable say res =INT_MIN, that hold the maximum palindrome number.
Run a loop from [0, n),  and check if(ispalindrome(arr[i]) && res<arr[i]), then set res = arr[i].
After complete iteration, check if(res==INT_MIN), set res = -1;
Print the value of res.
Longest palindrome in C
Method 1 : Code in C
Run
#include <stdio.h>
#include <limits.h>
int ispalindrome(int n){
     int rev=0, temp = n;

     while(temp>0){
          int rem = temp%10;
          rev = rev*10 + rem;
          temp /= 10;
     }

     if(n==rev)
        return 1;

     return 0;
}

int main(){
    int arr[] = {1, 121, 55551, 545545, 10111, 90};
    int n = sizeof(arr)/sizeof(arr[0]);
    int res = INT_MIN;

    for(int i=0; i<n; i++){

          if(ispalindrome(arr[i]) && res<arr[i])
             res = arr[i];

    }

    if(res==INT_MIN)
       res = -1;

    printf("%d ",res);
}
Output
545545
Related Pages
Finding the frequency of elements in an array

Sorting elements of an array by frequency

Counting Distinct Elements in an Array

Finding  Repeating elements in an Array

Finding Non Repeating elements in an Array

Method 2 :
In this method we first sort the array and then start traversing the array from end, and return the element that satisfy the condition, that it is palindrome.

Method 2 : Code in C
Run
#include <stdio.h>
#include <limits.h>
int ispalindrome(int n){
    int rev=0, temp = n;

    while(temp>0){
      int rem = temp%10;
      rev = rev*10 + rem;
      temp /= 10;
    }

    if(n==rev)
       return 1;

    return 0;

}

int main(){
    int arr[] = {1, 121, 55551, 545545, 10111, 90};
    int n = sizeof(arr)/sizeof(arr[0]);
    int j=n;

    for(int i=0; i<arr[j];i++){ 
int temp = arr[i]; 
arr[i] = arr[j]; 
arr[j] = temp; 
} 
int res = INT_MIN; 
for(int i=n-1; i>=0; i--){

     if(ispalindrome(arr[i])){
           res = arr[i];
           break;
       }

    }

    if(res==INT_MIN)
      res = -1;

    printf("%d ",res);
}
Output
545545
