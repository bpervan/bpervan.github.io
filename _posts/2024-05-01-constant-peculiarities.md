---
layout: post
title:  On const keyword and its peculiarities in C++
date:   2024-05-01 12:00:00
description: What you actually want to know about const in various spots in C++
tags: c++ programming computer-science english engleski
categories: computer-science
---

Did you ever get that feeling when rummaging through some C++ code that someone is fooling around with you? Or do you ever start to think if there was not a better way to achieve something in a language given what we wanted to enable the programmers to express? I tend to do, and I do it a lot. One of those things that keeps picking my need to approprietly classify and enumerate everything is the `const` keyword.

Keyboard `const` is a type modifier and shall be perceived as a part of the type. I tend to believe that once you start looking on it with that in mind, things become much clearer. As the name itself suggests, `const modifies the type in a way that it marks it as a constant, thus forcing the compiler to ensure that the programmer won't change the value of the variable that is declared constant, be it an ordinary data type, a pointer, or a reference.

Snippets that I used here are compiled and tested using `clang` v18 (upstream of the main branch at the momment, `llvm-project` repo, for what it's worth, the exact commit is `18170d0f`) without any special flags, just plain old `clang++ -o test test.cpp`

Even though `const` deals with data types, I'm going to split and demostrate its usage through the most-common meta use-cases.

## Variable declarations

### Part 1 - Initialization

Obviously, the simplest example is just declaring a variable a __const__-something:

```c++
const int variable = 10;
```

This will obviously fail:
```c++
//error: cannot assign to variable 'variable' with const-qualified type 'const int'
variable = 20;
```

Where the things get more interesting is when we introduce pointers (it nearly always gets interesting in C/C++ when we introduce pointers). If we factor in the fact that the variables can be declared as __const__ and non-__const__ and that the pointers to those variables can be declared as __const__ and non-__const__, this yields four different permutations:

1. Non-___const___ pointer to a non-___const___ value
```c++
int value = 10;
int* ptr = &value;

int another_value = 20;

//Value can be changed through the pointer
*ptr = 30;
//It can be changed what the pointer points to
ptr = &another_value;
```

2. Non-___const___ pointer to a ___const___ value
```c++
const int value = 10;
const int* ptr = &value;

//Value cannot be changed through the pointer, as it points to a const
//error: read-only variable is not assignable
*ptr = 50;

//But it can be changed what the pointer points to
const int another_value = 30;
ptr = &another_value;
```


3. ___Const___ pointer to a Non-___const___ value
```c++
int value = 10;
int* const ptr = &value;

//Value can be changed through the pointer, pointer is declared to be pointing to a non-const
*ptr = 50;

//But what the pointer points to cannot be changed
int another_value = 40;
//error: cannot assign to variable 'ptr' with const-qualified type 'int *const'
ptr = &another_value
```

4. ___Const___ pointer to a ___const___ value
```c++
const int value = 10;
const int* const ptr = &value;

//Value through the pointer cannot be changed, neither can what the pointer points to
const int another_value = 40;
//both should fail
//error: read-only variable is not assignable
*ptr = 20;

//error: cannot assign to variable 'ptr' with const-qualified type 'const int *const'
ptr = &another_value;
```

### Part 2 - Compatibility

Okay, now that we have grasped the basics, let's see what can be discussed regarding the compatibility of const and noncost types. At the end, those types should be similar to some extent, with those marked as consts begin somewhat limited.

You can
```c++
int noncstvalue = 20;
const int * noncstptr = &noncstvalue;

//but you cannot change the value through the pointer

//error: read-only variable is not assignable
*noncstptr = 30;
```


You are also not allowed to do this
```c++
const int value = 10;

//error: cannot initialize a variable of type 'int *const' with an rvalue of type 'const int *'
int * const cstpointer = &value;
```


```c++
//both pass
    //int* const cstptr = &noncstvalue;
    //const int* noncstptr = &value;
```

```c++
//(a)
    //This passes
    //you can assign a value of a const ptr to a noncstptr
    //int * const cstptr = &noncstvalue;
    //int * noncstptr = cstptr;
```

```c++
//(b)
    //This also works
    //you can assign a value of a noncst ptr to a cstptr
    //int * noncstptr = &noncstvalue;
    //int * const cstptr = noncstptr;
```

```c++
//This also works
    //you can assign to a noncstptr value of a cstptr
    //int * const cstptr = &noncstvalue;
    //const int * noncstptr = cstptr;
```

```c++
//Fails
    //error: cannot initialize a variable of type 'int *const' with an lvalue of type 'const int *'
    //const int * noncstptr = &noncstvalue;
    //int * const cstptr = noncstptr;
```

```c++
//Fails
    //error: cannot initialize a variable of type 'int *' with an lvalue of type 'const int *'
    //(c)
    const int * noncstptr = &noncstvalue;
    int * cstpt = noncstptr;
```


Const is more limiting qualifier. It is possible to cast nonconst to const, but vice versa is not allowed?

if i have a nonconst pointer, can i reassign it to a const pointer
if i have a const pointer, can i reassign it to a nonconst pointer

if i have a nonconst pointer
can i assign a const value?
can i cast a const value?

if i have a const pointer
can i assign a nonconst value?
can i cast a nonconst value?


Ultimately:
can i assign a ref of a nonconst value to a constant pointer
yes
```c++
//passes
    //int * const ptr = &noncstvalue;
    //*ptr = 30;
```

can i assign a ref of a constant value to a nonconstant pointer?
cant do this
```c++
    //fails
    //error: cannot initialize a variable of type 'int *' with an rvalue of type 'const int *'
    //int * ptr = &value;
```

## Parameter passing

```c++
struct Config{
    unsigned int id;
    const char* name;
};

int someFunction(const struct Config cfg){

}

int ptrFunction(const struct Config* cfg){

}

int ptrFunction(const struct Config& cfg){

}
```

## Class members

```c++
class Pair {
    private:
        int x;
        int y;
        
    public:
        int getX() const{

        }
        int getY() const{

        }
        int getSum() const{

        }
};
```