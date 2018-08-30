## Pointers and variables

#### What is a variable?
* it represents the name associated with the place in memory where it resides
* made up of:
  * a **name** --> the way of referencing the address location
  * a **type** --> a collection of different pre-defined values for things like the kind of values that can be stored, the encoding scheme and the total size in memory
  * an **address** --> the location in memory where the actual data is stored(can be physical or virtual)


###### Example
```C
int a = 3;
```
* variable "a" is of type **int** , which in C means that it holds 4 bytes in memory a.k.a 4 memory addresses
* when we refer to "a", we refer to the first memory address

---
#### Pointers
* it is like a variable, but instead of storing the data itself, **it stores the address** of where the data is to be found


```C
int *myPointer = &secretVariable
```
* "**\***" means "pointer"
* "**&**" means "address of"


###### More Examples

1. referencing a pointer
```C
// --- Example-1 ---
int a = 2;
int *pointerToA = &a; // declaration and defination of pointer;

// --- Example-2 ---
int *pointerToB; //declaration
int b = 3;

// * is only used for declaration.
pointerToB = &b; //defination


// --- Example-3 ---
int *pointerToArray;
int array[] = {1, 2, 3};

// & is not used in case of array.
// Remember array name itself a pointer to first element
pointerToArray = array;

// --- Example-4 ---
char *pointerToString;

// & is not used again. Remember a string is an array.
pointerToString = "hello";

// --- Example-5 ---
// declaration of two pointers
int *p1, *p2; // repeat * to declare another pointer.

// --- Example-6 ---
int* p1, v; // only p1 is pointer, v is interger variable
```

[Source](https://gist.github.com/theBeacon/02697753ae4d5343ce633e49adf9869d#file-pointer-declaration-c)


2. accessing the value at a pointer
```C
int a = 5;
int *pointerToA = &a;

a = 6;

// * is used as value-at operator
// whenever you use * outside declaration syntax, it is value-at symbol

// accessing value through pointer
printf("%d\n", *pointerToA); // print 6

// writing value to pointer
*pointerToA = 8;
printf("%d\n", a); //print 8

// taking new value from user
scanf("%d", pointerToA); // equivalent to scanf("%d", &a);

char hello[] = "hello";
char * pointerToHello =  hello;

// missing of '*' here : not needed for array or string
printf("%s\n", pointerToHello);
```

[Source](https://gist.github.com/theBeacon/d68bb4a73790c0282abc4c22edfd4ed0#file-value-at-c)

---

#### Important notes on pointers
* because the pointer only points to the first address in memory(just like a variable), the type of the pointer tells the compiler how many contiguous memory addresses to go from that address
* the size of the pointer can be dynamically allocated
###### Example
```C
/*
This program is in C, so malloc from stdlib.h is used
*/

int custom_size = 4;
char *myDynamicString = malloc(custom_size * sizeof(char))

int *myDynamicIntArray = malloc(custom_size * sizeof(int))

for(int i = 0 ; i < size ; i++)
{
  scanf("%d", &myDynamicIntArray[i])
}


```
