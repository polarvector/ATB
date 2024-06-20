# Automate the Boring
Automate the boring /w Py

# Functions
- arguments passed to a local variable (variable within a function) is a parameter

### The None Value

In Python, there is a value called None, which represents the absence of a value. The None value is the only value of the NoneType data type. (Other programming languages might call this value null, nil, or undefined.) Just like the Boolean True and False values, None must be typed with a capital N.

This value-without-a-value can be helpful when you need to store something that won’t be confused for a real value in a variable. One place where None is used is as the return value of print(). The print() function displays text on the screen, but it doesn’t need to return anything in the same way len() or input() does. But since all function calls need to evaluate to a return value, print() returns None. To see this in action, enter the following into the interactive shell: \

spam = print('Hello!') \
Hello! \
None == spam \
True \

---

### Stacks

| Python           | Microprocessors                                           |
|:------------------|:-----------------------------------------------------------|
| python           | microprocessors                                           |
| call stack       | stack where value from instruction pointer is pushed      |
| frame object     | address of the instruction pointer                        |

### Global and Local scopes (Containers)

The reason Python has different scopes instead of just making everything a global variable is so that when variables are modified by the code in a particular call to a function, the function interacts with the rest of the program only through its parameters and the return value.

Containers are useful because by using function parameters and return values, Python ensures that the only way a function can interact with the rest of the program is by:

    Receiving input through its parameters.
    Sending output through its return value.

Say we call a function that's supposed to return the value of a parameter 'No_of_eggs' (an argument attached to a local variable, in this case 'no_of_eggs'). Now suppose there's no such local variable but a variable exists with the same name in the global scope. The function will return value of the variable in the global scope.  

Example:
>def spam():\
>&nbsp;&nbsp;&nbsp;&nbsp;print(no_of_eggs)\
>no_of_eggs = 42\
>spam()\
>print(no_of_eggs)

**However**, this won't happen if there's an assignment statement within the function and will throw a 'variable referenced before assignment' error.

>def spam():\
>&nbsp;&nbsp;&nbsp;&nbsp;print(no_of_eggs)\
>&nbsp;&nbsp;&nbsp;&nbsp;no_of_eggs = 42\
>no_of_eggs = 7\
>spam()\
>print(no_of_eggs)


#### Remember these above two points
#### and BTW, local scope is destroyed when execution of a function is complete and global scope destructs when execution of the main program is complete. Meaning each time you access a function, a new local scop is created

### Exception handling

Code that might give an error during execution for a certain subset of inputs is written within **try** block. How the anticipated error is to be handled when such subset of inputs find their way are in the **except** block

Example:

>def spam(divideBy):\
>&nbsp;&nbsp;&nbsp;&nbsp;    try:\
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;        return 42 / divideBy\
>&nbsp;&nbsp;&nbsp;&nbsp;    except ZeroDivisionError:\
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;        print('Error, cannot enter zero')\
>print(spam(2))\
>print(spam(12))\
>print(spam(0))\
>print(spam(1))

**Note:** to write this program, we must have previous knowledge that dividing by zero gives ZeroDivisionError
