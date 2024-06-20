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
|------------------|-----------------------------------------------------------|
| python           | microprocessors                                           |
| call stack       | stack where value from instruction pointer is pushed      |
| frame object     | address of the instruction pointer                        |

