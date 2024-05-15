---
tags:
  - programming
  - diagram
  - structure
---

![[Pasted image 20240509110057.png]]

Each of these functions has a name by which we can call it. To *call* a function is to **execute** the code statements contained inside that function. At its core level, this provide us, programmer, with less lines to type. 

Each program has an *entry-point* expected by the compiler to be there. That entry-point is a function called *main*. The code you write inside the *main* function is the first code that executes in your program, and therefore it is responsible for calling any other functions in your program. 

You may be asking yourself, but who calls the *main* function? The operating system!

![[Pasted image 20240509111241.png]]

### Arguments Vs Parameters
We can tell the difference between the two by looking at where it is coming from. If we are referring to a variable passed into a function when we call it, then it's an argument. If the variable is in the definition of a function rather than where we call it somewhere else, then it is referred to as the parameter. See the code below for an example:
```C
void myFunction(int parameter1, int parameter2) { 
//todo: code 
} 

int main() { 
	int argument1 = 4; 
	int argument2 = 5;
	myFunction(argument1,argument2); 
	return 0; 
}
```


