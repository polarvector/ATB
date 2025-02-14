# Automate the Boring
Automate the boring /w Py \
**Remember, user inputs are always of data-type str (string)**

# Functions
- arguments passed to a local variable (variable within a function) is a parameter

### The None Value

In Python, there is a value called None, which represents the absence of a value. The None value is the only value of the NoneType data type. (Other programming languages might call this value null, nil, or undefined.) Just like the Boolean True and False values, None must be typed with a capital N.

This value-without-a-value can be helpful when you need to store something that won’t be confused for a real value in a variable. One place where None is used is as the return value of print(). The print() function displays text on the screen, but it doesn’t need to return anything in the same way len() or input() does. But since all function calls need to evaluate to a return value, print() returns None. To see this in action, enter the following into the interactive shell:

spam = print('Hello!') \
Hello! \
None == spam \
True

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

### Lists

Tip : Read indexing like this as 'from zeroth element to 3rd from last element'
Example:
spam = ['cat', 'bat', 'rat', 'elephant', 'moron', 'dick', 'bastard']
spam[0:-3]

<u>Output</u> 
['cat', 'bat', 'rat', 'elephant']

### Distinction between Method and Functions
methods are same as functions except that are "called on" values in the following way:

spam.index('rat')

This is distinct from how you would use something like random.shuffle(spam)

In the Method, we're following the value we want to operate on with a dot '.' and writing the function we want to attach to it to get a certain result.
While in functions, we pass a value to the function as an argument

Also, each data type has certain methods that come with it.

The Distinction:
| Type     | Way to use                                |
|:---------|:------------------------------------------|
| Method   | value.functionality(some element of value)|
| Function | function(value)                           |

#### Table of methods for a list

The Distinction:
| Method     | Example                  |
|:-----------|:-------------------------|
| index      | spam.index('rat')        |
| remove     | spam.remove('bat')       |
| sort       | spam.sort()              |
|            | spam.sort(reverse=True)  |
|            | spam.sort(str.lower)     |
| reverse    | spam.reverse()           |
| append     | spam.append()            |
| insert     | spam.insert(index,'bat') |

![image](https://github.com/x747/ATB/assets/72918894/f1c64a9c-ec27-4fa0-a211-03f4cfc43bd3)

#### handy keywords

>name = 'Sphinx'\
>'nx' in name 

This gives out true if 'nx' is present in our string. It's inverse is **not in**

#### Remember, strings are immutable unlike lists. This is meaningful in Passing References apparently. We shall see.

### Tuple

Unlike lists, tuples are **immutable**
Pass a list as an argument to tuple() to turn it into a tuple. Likewise, do the vice-versa to convert tuple into list and make it mutable 

>myTuple = ('say','my',7,'name')\
>eggs = (1,) # use trailing comma to specify that it's a tuple you want. Works for int, str, float, etc. all basic data types

### Passing References

in this code:

>def eggs(someParameter):\
>&nbsp;&nbsp;&nbsp;&nbsp;someParameter.append('Hello')\
>spam = [1, 2, 3]\
>eggs(spam)\
>print(spam)

in this example, although spam and someParameter contain separate references (they point to different memory addresses), they both refer to the same list. This is why passing it as an argument to a function and modifying it modifies it while in case of other variables, the modification happens locally within the function only.

#### copy module - helps copies values inside a varible to a separate address without affecting original referencing
#### a variant deepcopy() copies the inner lists in a list as well

### Dictionaries

Dictonaries aren't ordered and indexed like lists or tuples. Therefore
> eggs = {'name': 'Zophie', 'species': 'cat', 'age': '8'}\
> ham = {'species': 'cat', 'age': '8', 'name': 'Zophie'}\
> eggs == ham
returns **TRUE**

They are indexed by their keys. i.e eggs[species] will return 'cat'

using checking operators like:
> if name in birthdays:

checks if name is a key in the dictionary, not if name is the key-value



#### Methods

>eggs.keys()

returns keys. **Data type** : **dict_keys**

>eggs.values()

returns values. **Data type** : **dict_values** 

>eggs.items()

returns keys and values as a tuple **Data type** : **dict_items**

**NOTE:** pass results to a list to obtain one

**get()** method 
>eggs.get('cups',0)

checks dictionary keys for 'cup' and returns corresponding value. If the key isn't present, it returns 0 or anything you pass as a 2nd argument

**setdefault()** method
>eggs.setdefault('cups','red')

checks for the key 'cups' and returns it's corresponding value. However, if the key isn't there it places a value 'red' associated with a new key 'cups' in the dictionary. Useful for on-the-fly addition to a database. **Very cool**

### OMG Dictionaries are fun. In love with them already!


### Comparison table of how lists, tuples & dictionaries differ & their main methods

| Type  | typed as                  | indexed as [Py always uses big brackets for indexing] |
|:------|:--------------------------|:------------------------------------------------------|
| List  | list = [1,2,3]            | list[0]                                               |
| Tuple | tuple = (1,2,3)           | tuple[0]                                              |
| Dict  | dict = {'1st':1, '2nd':2} | dict['1st']                                           |

## Manipulating Strings

| **Method**                | **Input**                     | **Output**          | **Usage**                                              |
|---------------------------|-------------------------------|---------------------|--------------------------------------------------------|
| `upper()`                 | `'hello'`                     | `'HELLO'`           | Converts a string to uppercase.                        |
| `lower()`                 | `'HELLO'`                     | `'hello'`           | Converts a string to lowercase.                        |
| `isupper()`               | `'HELLO'`                     | `True`              | Checks if all characters are uppercase.                |
| `islower()`               | `'hello'`                     | `True`              | Checks if all characters are lowercase.                |
| `isalpha()`               | `'Hello'`                     | `True`              | Checks if all characters are letters.                  |
| `isalnum()`               | `'Hello123'`                  | `True`              | Checks if all characters are alphanumeric.             |
| `isdecimal()`             | `'12345'`                     | `True`              | Checks if all characters are numbers.                  |
| `isspace()`               | `'   '`                       | `True`              | Checks if all characters are whitespace.               |
| `istitle()`               | `'Hello World'`               | `True`              | Checks if string is in title case.                     |
| `startswith('substring')` | `'Hello World'`               | `True`              | Checks if string starts with 'substring'.              |
| `endswith('substring')`   | `'Hello World'`               | `True`              | Checks if string ends with 'substring'.                |
| `join(['list', 'of', 'strings'])` | `['cats', 'rats', 'bats']` | `'cats, rats, bats'` | Joins list of strings with the specified delimiter.    |
| `split()`                 | `'Hello World'`               | `['Hello', 'World']`| Splits a string into a list of substrings.             |
| `rjust(width)`            | `'Hello'`                     | `'     Hello'`       | Right justifies a string to a specified width.         |
| `ljust(width)`            | `'Hello'`                     | `'Hello     '`      | Left justifies a string to a specified width.          |
| `center(width)`           | `'Hello'`                     | `'  Hello  '`       | Centers a string within a specified width.             |
| `strip()`                 | `'   Hello   '`               | `'Hello'`           | Removes whitespace from the beginning and end.         |
| `ord('A')`                | `'A'`                         | `65`                | Returns the Unicode code point of a character.         |
| `chr(65)`                 | `65`                          | `'A'`               | Returns the character from a Unicode code point.       |
| `pyperclip.copy('text')`  | `'Hello, world!'`             | (Copies 'Hello, world!' to clipboard) | Copies 'text' to the clipboard.                |
| `pyperclip.paste()`       | (Clipboard contains `'Hello, world!'`) | `'Hello, world!'`   | Retrieves text from the clipboard.                     |

## Regular Expressions a.k.a. RegEx

>> import re #expression to import regular expressions module

#### Methods:

myRegEx = re.compile() -> creates RegEx object. Input RegEx in parentheses
can also pass re.I as 2nd argument to re.compile for case-insensitivty



matches = myRegEx.search() -> searches for a match in the input string

matches.group(1) -> if RegEx has multiple groups, returns results categorically

myRegEx.findall() -> finds all occurences of the input string

#### Character Classes

| **Character Class** | **Represents**                          |
|:--------------------|:----------------------------------------|
| `\d`                |Any numeric digit from 0 to 9.           |
| `\D`                |Any numeric digit from 0 to 9.           |
| `\w`                |Any letter, numeric digit, or the underscore character. (Think of this as matching “word” characters.)    |
| `\W`                |Any character that is not a letter, numeric digit, or the underscore character.      |
| `\s`                |Any space, tab, or newline character. (Think of this as matching “space” characters.)     |
| `\S`                |Any character that is not a space, tab, or newline.     |
|custom `[chars_here]`|[aeoAEO] or [a-zA-Z0-9]                  |
Custom **Character Classes**
>> specific_vowel_regex = re.compile(r'[aeouAEOU]')
this code matches any lower or uppercase vowels

Can also include ranges of letters or numbers by using a hyphen. For example, the character class [a-zA-Z0-9] will match all lowercase letters, uppercase letters, and numbers.

#### Regex Symbols Summary

    ? matches zero or one of the preceding group.
    * matches zero or more of the preceding group.
    + matches one or more of the preceding group.
    {n} matches exactly n of the preceding group.
    {n,} matches n or more of the preceding group.
    {,m} matches 0 to m of the preceding group.
    {n,m} matches at least n and at most m of the preceding group.
    {n,m}? or *? or +? performs a non-greedy match of the preceding group.
    ^spam means the string must begin with spam.
    spam$ means the string must end with spam.
    . matches any character. More dots = more characters, except newline characters.
    \d, \w, and \s match a digit, word, or space character, respectively.
    \D, \W, and \S match anything except a digit, word, or space character, respectively.
    [abc] matches any character between the brackets (such as a, b, or c).
    [^abc] matches any character that isn’t between the brackets.



