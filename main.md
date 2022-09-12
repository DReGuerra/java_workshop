# Java Workshop
Andre Guerra \
June/2022 \
andre.guerra@mail.mcgill.ca

This workshop is currently being developed. Below is a list of contents that will be expanded. The topics in each of these sections are not exhaustive of the entirety of the Java language. I will try to fill out the "meat" of the contents first, and once the workshop has taken more shape, I will start to polish existing content and add more advanced topics/features.

---
*Note:* Most of the topics covered on this files are general programming mechanisms (e.g., if-else, types of loops, or exception handling). As such, these are applicable to a variety of programming languages (although syntax may vary). This means that this workshop can provide you with the key concepts (classes, encapsulation, inheritance, and polymorphism) for implementing OOP in most other language.

---
## Contents
0. Getting started
1. Developing in Java
2. Programming basics
3. Flow control
4. Classes
5. Inheritance
6. Polymorphism
7. Abstract classes
8. Exception handling
9. Interfaces

---
## Getting started
Before getting started coding in Java you will need an integrated development environment (IDE). There are a variety of possible options to be used (e.g., [Eclipse](https://www.eclipse.org/downloads/), [NetBean](https://netbeans.apache.org/), [BlueJ](https://www.bluej.org/), etc.). I will use [IntelliJ IDEA](https://www.jetbrains.com/idea/). Follow the links and download the IDE you are most interested in. 

Now that you downloaded an IDE, you need to download Java. Java Standard Edition (SE) 18 is the latest version, while Java SE 17 is the long term support (LTS) version. You will need to download Java SE 17 or 18 and the Java Development Kit (JDK) 18 that accompanies them. The JDK contains the development environemnt with which Java programs can be developed. You can download these on the Oracle [website](https://www.oracle.com/java/technologies/downloads/#java18).

---
## Developing in Java
There are several benefits for developing in Java. One of the most important ones is Java's handgling of the program from high-level code (the Java code itself) down to low-level code (machine code) which the compute executes. Generally, programming languages translate the high-level code to low-level code via a compiler. The compiler converts your high-level code directly to the machine code of your computer. The problem is that different computers use different machine languages, which means to run your program in different computers you need to compile it with different compilers. Java solves this problem through the implementation of the Java Virtual Machine (JVM). 

The JVM compiles your high-level Java code to byte-code. Byte-code is the machine language of a JVM. A JVM is a virtual JAVA computer that is running inside your computer (comes from the JDK that we downloaded in the previous section). Now, since the JVMs running on all computers that download the JDK are the same, the byte-code is tranferable between computers. Finally, the JDK will also perform a Just-In-Time (JIT) compiling of the byte-code. This happens as the compiler converts the byte-code to machine code chuck by chuck throughout the execution of the program (just-in-time).

---
## Java basics
### `main` method
The simplest Java program will have only one class, and in that class there will be one method called `main`. This method contains the commands that will accomplish the desired tasks for the Java program. Below is an example:
```
Public class SimplestClass()
{
    public static void main(String[] args)
    {
        int a = 1;
        int b = 7;

        System.out.println("This class prints a line.");
        System.out.println("Then it performs a calculation, and outputs the result.");

        c = a + b;

        System.out.println("a = " + a);
        System.out.println("b = " + b);
        System.out.println("a + b = " + c);
    }
}
```
The output of this program is:
```
    This class prints a line.
    Then it performs a calculation, and outputs the result.
    a = 1
    b = 7
    a + b = 8
```

### Output to console
Regarding the output in the previous example, the command `System.out.prinln()` was used to print to the console. `println()` takes a `String` argument to output to the console. `System.out.print()` may also be used, but the difference is that `prinln()` includes an implicit new line character when it is executed, while repeated uses of `print()` will result in outputo on the same line. Notice that comments are denoted with `//` in Java.
```
Public class SimplestClass()
{
    public static void main(String[] args)
    {
        System.out.println("This prints with a new line character; go to the next line.");
        System.out.print("This does not include new line character ");
        System.out.print("so repeated use outputs to same line.");
        System.out.println(); // prints a new line
        System.out.print("End of program.);
    }
}
```
The output of this program is:
```
    This prints with a new line character; go to the next line.
    This does not include new line character so repeated use outputs to same line.
    End of program.
```
Another method to output to the console is `printf()`, which allows for the specific formatting of the output string. Below is an example.
```
Public class SimplestClass()
{
    public static void main(String[] args)
    {
        double weight = 159.78;
        System.out.print("The weight is: ");
        System.out.prinf("%5.1f", weight);
        System.out.prinf(" lbs.");
    }
}
``` 
The output of this program is:
```
    The weight is: 159.8 lbs.
```
In the method `printf()` we use the format spcifier `"%5.1f"`. This specifier indicates that we want to format the output in a width of 5 characters (the decimal point counts) with exactly 1 decimal place. So, 159.78 becomes 159.8.

### Variables, constants, and their assignment
Java is a case sensitive language, and identifiers can contain letters, digits, and "_", but cannot start with a digit. This means that `firstname`, `FirstName`, `firstName` are all acceptable identifiers and independent locations in memory will be used to store each of them once values are assigned.

Variables must be declared before use. This involves specifying its type. Variables and constants in Java may be cast to various primitive types. These include `byte`, `short`, `int`, `long`, `float`, `double`, `boolean`, or `char`. The class `String` is a pre-made class available in Java in which variables of type String hold a series of `char` type characters and they are defined with double quotation marks.

Below are some examples of declarations and assignments:

```
    int a = 1;                  // declaration and assignment
    double weight;              // declaration only
    int i, j, k;                // declaration of multiple variables for type int
    boolean done = false;
    char grade = 'B'
    String firstName = "John"   // String class type
    String lastName = "Smith"
    
```
### Naming conventions
There are several naming conventions that dictate how variables, objects, classes, etc. should be named in different programming languages. Here are some of the important ones for Java development.

`camelCase` $\rightarrow$ variables (e.g., `firstName`) and methods (e.g., `calculateAge`) \
`PascalCase` $\rightarrow$ classes (e.g., `Students`), interfaces (e.g., `IHuman`) \
`CONST_CASE` $\rightarrow$ constants (e.g., `PI`, `USD_CAD`) \
`lowercase` $\rightarrow$ packages (e.g., `statslib`)

---
## Flow control
### Branching mechanisms
The branching mechanisms used in Java are similar to C and C++ (and other languages). Below is a quick review of `if` statements and some of its variants. While going over the examples below, keep in mind a few things:
- the boolean conditions must be between brackets
- if the boolean condition is evaluated to `true` then the statement immediately after it is executed, otherwise flow is sent to the next statement
1. Standard `if-else` statements
    These statements have two parts, the `if` and the `else`. The `if` is executed if the boolean condition is evaluated to true.
    ```
    int age = 24;
    if (age > 21)
        System.out.println("I'm over 21!");
    else
        System.out.println("I'm not over 21.");
    ```
    Output:
    ```
    I'm over 21!
    ```
2. Simple `if` statements
    Simple `if` statements have statements that are executed when the boolean condition is evaluated as `true`.
    ```
    if (elevator == currentFloor)
        door.open()
    ```
3. Multiple condition `if-else` statements
    `else` statements can be used for creating more complex behaviour depending on the desired conditions. Notice here the usage of curly brackets to form the blocks in the if-else statements. These are not necesary here, but they become necessary if any one statement contains more than one line of code.
     
    ```
    float currentCash = 14.35;
    if (currentCash > 35.00){
        System.out.println("You can buy a steak.");
    } else if (currentCash > 20.00){
        System.out.println("You can buy a pizza.");
    } else if (currentCash > 10.00){
        System.out.println("You can buy a burger.");
    } else{
        System.out.println("You don't have enough money to eat here.);
    }
    ```
    Output
    ```
    You can buy a burger.
    ```
Additionally, you can nest any of the types of if-else statements above to create more complex behaviour.

### Switch statement
In a switch statement, one of a series of "case" statements are executed dependant on the controlling expression value. The switch statement also includes a `default` case that will run if the controlling expression does not take the value of any of the cases.
```
switch {controlling_expression}
{
    case case_name_1:
        statements;
        break;
    case case_name_2:
        statements;
        break;
    default:
        statements;
        break;
}
```
Each case must end with a `break` statement to prevent the flow to continue into the next case. This feature allows us to implement two conditions for one case:
```
int name = 'Tom';

switch {name}
{
    case 'Tom':
    case 'Jerry':
        statements;
        break;
    default:
        statements;
        break;
}
```

### Loops

TODO: 
- loops (for, while, do-while)
- break, continue, exit
- if-else statements

---
## Classes

TODO:
- concept of a class
- objects
- instances
- constructors
- attributes
- methods
- 3 main features that allow for OOP: Encapsulation, Inheritance, Polymorphism

---
## Encapsulation

---
## Inheritance

TODO:
- concept of a child class
- inheritance from parent class

---
## Polymorphism


## Abstract classes
Classes in which some methods are not fully defined - they are abstract methods.

TODO:
- abstract methods

---
## Exception handling

TODO:
- try-catch-throw
-

---
## Interfaces

