---
layout: post
title: "C behavior(scanf and fgets)"
---



# fget() and scanf() functions and their behavior<br>

 The `fgets()` is a standard version of the `gets()` function.`gets()`function has long been obsolete
 because it would prepare the system memory to receive any input value without any prediction;
 And this could cause overflow.
 But the `fgets()`reduces this possibility by restricting the input.
 ```c
 #define Max 100  
 char str[Max];
 fgets(str,Max,stdin);
 ```
<br>

 `scanf()` is also a function for receiving input,
 which stores the value in a variable by specifying the input format
 and passing a pointer to that variable.

 ```c
 int item;
 scanf("%d",&item);
 ```
<br>

 But using these two functions in succession can be problematic.
 If you place the `fgets()` immediately after the `scanf()`,

 ```c
    printf("%s\n","Enter a number and a sentence :");
    int data;
    char str[Max];
    scanf("%d",&data);
    fgets(str , Max , stdin);
 ```
<br>

 What happens is that the program waits while running until you enter a number.
 After you enter a number and press Enter,
 the program skips the `fgets()` and does not receive a sentence.
 If we look more closely, the program actually doesn't jump over the `fgets()`.
 In fact, when you press Enter, the program gives the entire space 
 after the number to the next line to `fgets()` with the same Enter key.
 So in practice, nothing is stored except `SPACE` inside str.
 The simple solution to this is like this: '\\n'  

 ```c
    printf("%s\n","Enter a number and a sentence :");
    int data;
    char str[Max];
    scanf("%d\n",&data);
    fgets(str , Max , stdin);
 ```
<br>

This will cause the program to wait for the next line to enter a sentence.
