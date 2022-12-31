Author : Mehdi Lahlou Mimi

_______________________________________________________________________________
## Hello World program

Here is the hello world program code to be executed in Go :

```
package main  
import "fmt"  
  
func main() {  
  fmt.Println("Hello World!")  
}
```

In order to run this on the terminal, you've gotta run this command : 
```
go build .\helloworld.go
```
It is essential because <span style="color:cyan">Go is compiled</span>


## Generalities about the syntax

* The `fmt` package is the <span style="color:red">standart library </span> of the Go langage.
* You need to declare the name of the program you're writing.
* In go, you don't need to use `;` you can just break the line or use it to write multiple instructions in a single line this way : 
```
instr1; instr2;....;
```
* Commands work the same way as C or javascript.

## Variables

### Variable declaration

There are two ways to declare a variable : 
```
var name = value (1)

// or

name := value    (2)
```

The difference between these two methods is that (1) <span style="color:green">can be used inside and outside function</span> but (2)  <span style="color:green">can be used inside functions only</span>. This must be remembered for debugging.
Also, Variable declaration and value assignment *can be done separately* in (1) and not for (2).
Which is logical.

In order to declare a variable without initializing a value we can do this : 
```
var name type
```

For multiple variable declaration we can do this : 
``
```
var name1, name2, ... = val1, val2, ...
```

    For variable naming, it follows the same rule as python, generally code editors
    notice these errors and prevent us from doing them.   

### Types in Go 

* int
* float32
* string
* bool

## Constants 

Go do support constants and this is how we declare them : 
```
const PI = 3.14;
```

    Constants do follow the same naming rule as variables

<span style="color: purple">We are not obliged to put them uppercase, but programmers are just accustomed to</span> 
There are two types of constants 

### Typed constants

These are the constants that we declare <span style="color:cyan">with their types</span>.

### Untyped constants

These are the constants that we declare <span style="color:cyan">without their types</span>.

### Multiple constant assignement

It goes like this : 

```
const (
   name1 int = val1
   name2 = val2
   ...
   ...
   ...
)
```

## Output functions

### `Print()`
It is the *raw* output method, and print the content to its default format.
<span style="color:cyan">It doesn't add a whitespace between parameters.</span> 
If two `Print()` statements are followed, it will output the results in the same line.
We will need a `"\n"` to avoid this problem, like this : 

```
fmt.Print(i)
fmt.Print("\n")
fmt.Print(j)
```

### `Println()`
It works like the previous one with the difference that a whitespace is added between the parameters and a newline is added in the end.

### `Printf()`
It does the output like the first function but do make a formatting of these : 
* `%v` : Formatted to the value of the variable
* `%T` : Transformed into the type of the variable

### Formatting verbs

| Type    | Verb | Instruction   |
| ------- | ---- | ------------- |
| Integer | `%b` | Base 2        |
|         | `%d` | Base 10       |
| String  | `%s` | Whole string  |
|         | `%q` | Double quoted |
| Bool    | `%t` | Value         |

For more verbs you can visit [this page](https://www.w3schools.com/go/go_formatting_verbs.php)

## Data types

Basically, the Go standart library only supports 2 data types : 
* Numeric (integers, floats...).
* Boolean.
* String.

### Integers

###### <span style="color:yellow">Signed integers</span>
These can store both positive and negative integers.

###### <span style="color:yellow">Unsigned integers</span>
They are declared with the `uint` keyword and they can only store non-negative values

## Arrays

### Declaring arrays
In order to declare arrays we follow this schema : 
```
var array_name = [length]datatype{value1, value2, ...} (1)
array_name := [length]datatype{value1, value2, ...}

// or

var array_name = [...]dataype{value1, value2, ...} (2)
array_name := [...]datatype{value1, value2, ...}
```

In Go <span style="color:cyan">arrays have a fixed length</span> so for the (2) method, the number of elements you'll put is going to be the final length of the array.

### Accessing elements of an array

Like all the other languages, it can be done by specifying the index of the element inside `[]` 
this way : `array[element]`
<span style="color:purple">It is counted starting from 0</span> 

### Changing the elements of an array

This way : 
```
// To change the i-th element of an array
my_array[i] = new_value
```

### Array initialization

Three ways of doing it : 

```
arr1 := [l]datatype{} //not initialized
arr2 := [l+2]dattype{a, b} //partially
arr2 := [l]datatype{a_1, a_2, ..., a_l} //fully
```

<span style="color:yellow">In order to choose specific elements to initialize we do this : </span>
```
array_name := [l]datatype{l_1:value_1, l_2:value_2, ... l_n:value_n}
```
	Here we initialize only the l_1, l_2,... l_n values, the rest is going to be a null
	value (depending on the datatype)

	To find the length of an array we use the `len` function

<span style="color:cyan">Array can store values of the same datatype and nothing else</span>

## Slices 
In Go, slices are like arrays but they differ in the point that slices have a dynamic size, they can grow or shrink with a maximum number of elements called capacity depending on what we want

### Slice declaration
It follows this syntax : 
```
slice_name := []datatype{values}
```

<span style="color:cyan"> To get the capacity of a slice we use </span>` cap `  <span style="color:cyan">function and for the length the</span> ` len ` <span style="color:cyan">one</span>

### Create a slice from an array
We do it following this syntax : 
```
myslice := array[start_index:end_index]   // the element at end_index isn't included
```

### Using the make() function

Here is the syntax : 
```
slice_name := make([]type, length, capacity)
```

The syntax here up gives an array with length number of zeroes 

	In order to access an element from a slice we use the [i] syntax like arrays. Same for modifying the
	element at the i-th place   


	It is possible to change a slice's length by re-slicing an array another time

### Appending two slices
In Go, we can create another slice by combining two existing ones by doing `append(myslice1, myslice2,...)` that actually creates a third slice that the capacity <span style="color:yellow">is the sum of all the slices' capacities</span>. 

### Memory efficiency
In Go, all the slices elements are loaded and ready to be used. If we don't need them all and in order to optimize the memory we can make a copy of a slice inside a smaller one using the `copy` function

Syntax : 

```
copy(destination, source)
```


## Go Operators

Here is (mostly) complete chart of go operators 
| Type        | Name                  | Description                                                                                             | operator | Code       |
| ----------- | --------------------- | ------------------------------------------------------------------------------------------------------- | -------- | ---------- |
| Arithmetic  | Addition              | Adds two values                                                                                         | +        | `x+y`      |
|             | Substraction          | Does the substraction                                                                                   | -        | `x-y`      |
|             | Multiplication        | Does the multiplication                                                                                 | *        | `x*y`      |
|             | Division              | Does the division                                                                                       | /        | `x/y`      |
|             | Modulus               | Gives the rest of the euclidiant div                                                                    | %        | `x%y`      |
|             | Increment             | Increments a value (+1)                                                                                 | ++       | `x++`      |
|             | Decrements            | Decrements a value (-1)                                                                                 | --       | `x--`      |
| Assignement |                       | Sets the value                                                                                          | =        | `x=val`    |
|             |                       | Increase the value by val                                                                               | +=       | `x+=val`   |
|             |                       | Decreases the value by val                                                                              | -=       | `x-=val`   |
|             |                       | Multiplies the value by val                                                                             | `*=`     | `x*=val`   |
|             |                       | <span style="color:blue">Works with every operator</span>                                               |          |            |
| Comparison  | Equal to              | Returns if the values are equal                                                                         | ==       | `x==y`     |
|             | Not equal             | Returns if the values aren't equal                                                                      | !=       | `x!=y`     |
|             | Greater than          | Returns if a values is greater                                                                          | >        | `x>y`      |
|             | Lesser than           | Returns if a values is lesser                                                                           | <        | `x<y`      |
|             | Greater than or equal | Returns if a values is greater or equal                                                                 | >=       | `x>=y`     |
|             | Less than or equal    | Returns if a values is less or equal                                                                    | <=       | `x<=y`     |
| Logical     | Logical and           | If both statement are true                                                                              | &&       | `(x)&&(y)` |
|             | Logical or            | If one of the statements is true                                                                        | `||`     | `(x)||(y)` |
|             | Logical not           | Reverses the result                                                                                     | !        | `(x)!(y)`  |
| Bitwise     | AND                   | 1 if both bits are 1                                                                                    | &        | `x&y`      |
|             | OR                    | 1 if one is 1                                                                                           | `|`      | `x|y`      |
|             | XOR                   | 1 if only one is 1                                                                                      | ^        | `x^y`      |
|             | Zero fill left shift  | Shift left by pushing zeros to the right                                                                | <<       | `x<<2`     |
|             | Signed right shit     | Shift right by pushing copies of the leftmost bit in from the left, and let the rightmost bits fall off | >>       | `x>>2`     |
                                                                                                                                |          |            |

<span style="color:yellow">These operators cannot be used in the variable naming</span>

## Go conditions
Conditions are the most popular way to control the flow of a program execution, it is mainly used with Logical operators to use boolean statements as activators.
Here is the general syntax : 
```
if _condition1_ {  
   _// code to be executed if condition1 is true_ 
   if _condition1.1_ {
	   __// code to be executed if condition 1.1 is true__
   } 
} else if _condition2_ {  
   _// code to be executed if condition1 is false and condition2 is true_  
} else {  
   _// code to be executed if condition1 and condition2 are both false_  
}
```

<span style="color:purple">You must be familiar with conditions, as every programmer should be, this section is just about the syntax</span>

## Go switch
Switch case is another famous way to control the flow of execution of a program

### Single case

```
switch _expression_ {  
case _x_:  
   _// code block_  
case _y_:  
   _// code block_  
case _z_:  
...  
default:  
   _// code block_  
}
```

### Multi case
```
switch _expression_ {  
case _x_,_y_:  
   _// code block if expression is evaluated to x or y_  
case _v_,_w_:  
   _// code block if expression is evaluated to v or w_  
case _z_:  
...  
default:  
   _// code block if expression is not found in any cases_  
}
```

Instead of writing the same code for `__x__` case and `__y__` one, we put them all together in the same line

	the `default` section acts as the `else` of an if-statement
