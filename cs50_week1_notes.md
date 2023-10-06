# Week 1

**Source code** is any computer programme, written in any programming language by a programmer, intelligable to humans. **Machine code** is the converted form of **source code**, which is intelligable to a computer as **binary**, but unintelligable to humans. **Source code** is transformed into **machine code** by a **compiler**. In this instance, you are using VSCode to compile your programme. VSCode is a **source code** editor that features debugging, syntax highlighting and **compiling**, amongst other functions. Although it is not strictly an **Intergrated Development Environment (IDE)**, that is a software with greater native functionality, VSCode's many extensions bring it close.

_What constitutes 'good' programming? That which is fast, maintainable and elegantly communicates your solution. Or, you could say, that which is correct, well-designed and well-styled._ If there is a lot of _'copy & paste' programming in your programme it is a sign of bad design_. You want to have to change a **value** in one location withing the programme, not in every single instance. This would be an oppertunity to **abstract** away the *low-level* complexity of your **algorithims** in favour of the elegance of a *high-level*, bespoke **function**. Or a **loop**, perhaps?

Your **terminal** provides a **command line interface (CLI)** within which you can command the computer to execute certain actions. Users and computers can also interact via a **graphical user interface (GUI)**, which consists of icons, like on a desktop or smartphone screen. If nothing appears in your **CLI** after you return a command to execute, it is normally a good sign that what you wanted has happened.

## C

Convention is to *not* capitalise any filenames you create.

- `/n`: An **escape sequence** which programmes a line break in to the output. Its inclusion will move the **CLI** cursor on to a new line once your programme has ran and keep everything visually tidy. This too is conventional.

- **Libraries**: Collections of additional functions a programme might need to implement but that are not natively featured within the language, possiblity due to resource constrains and impracticality. To find out what functionality a language features natively and what **libraries** are available, *always* refer to the **documentation**. To import a **library** to **C**, write the **statement**, i.e., a self-enclosed 'sentence' of programming, `# include <library>` at the head of your programme.

- **Return Value**: A **value** resultant of **calling** a **function** that can be reused, where as a **side effect** is an 'inert', *visual* resultant, like 'hello, world' printing to your **terminal**. In terms of the 'Black Box': ***argument> function> return value***.

- **Compiling** and **Running**: In **C** your programme must be **compiled** before it can run and *must* be without errors for it to **compile**. First, create a file by executing the command `code new_prog.c`. This is where your **source code** will reside. `code` is a command specific to VSCode. Next, execute the command `make new_prog`, where `make` **compiles** by searching for a .c file of the given name to transform in to **machine code**. Finally, the executable file `new_prog` will be created and is where the computer-intelligable **machine code** resides. To run `new_prog` execute the command `./new_prog`. `./` is the universal command to run any file in your ***working*** **directory**.

- **Calling**: The act of triggering a **function**, i.e., **calling** it to action. In **C**, the syntax `;` at the end of a **statement** is the signal to **call**.

- **Variables**: Are 'containers' for **values**. **Values** can change depending on **conditions** being met elsewhere in the programme, such as a user input. In the below example, we will see the variable `answer` is **assigned** by the syntax `=` to whatever **value** the **function** `get_string` has returned to it by a user prompted with the **argument** "What's your name? ". At the beginning of the **statement**, `answer`'s data type is declared a `string`. This signals to the programme that the **return value** must be a sequences of characters, i.e., a `string`. In **C**, once a **variable** has had its data type initially signalled, the programme does not require it to be declared again.
   
    #include <cs50.h>
    #include <stdio.h>

    int main(void)
    {
        string answer = get_string("What's your name? ");
        printf("hello, %s\n", answer);
    }

- **`printf`**: A **function** that outputs the outcome of an **argument**. In the above example, **C** requires the syntax `%s` be used as a stopgap within our **argument** for the resultant **value** of our `answer` **variable** . The `answer` **variable** is subsequent a `,` and outside quotation marks, the presence of which indicates that they contain a `string`. Finally, like `get_string`, the **function** is **called** by the syntax `;`.

- **Conditionals**: In the below example you will see that the **conditional** **keywords** `if` and `else` take account for all potential outcomes of the preceeding **arguments**. Furthermore, there is a single space after `if` and before the brackets which was not present when programming **functions**, like `printf()`, `get_int()` and `get_string()`.

    #include <cs50.h>
    #include <stdio.h>

    int main(void)
    {
        int x = get_int("What's x? ");
        int y = get_int("What's y? ");

        if (x < y)
        {
        printf("x is less than y\n");
        }
        else if (x > y)
        {
        printf("x is greater than y\n");
        }
        else
        {
        printf("x is equal to y\n");
        }
    }

- **Loops**: Are a category of command that facilitates *recursive execution* of sections of programming. This is useful when a certain **condition** needs to be under constant check, such as the validity of a user input. **Loops** also make your programme tider than a succession of 'copy & paste' code for every concieveable **condition**.

In the below example `i` as been **assigned** the **value** 0, which will increase by 1 after every **loop** thanks to the **operation** `i++`; in this sense, `i` is acting as a counter. The **keyword** `while` initialises a **loop** by acting as the signal that the succeeding programming is under constant check for a certain **condition**. How the programme will execute next depends on whether the **condition** of the `while` **loop** is presently met or unmet, `True` or `False`; a **boolean** expression. The **condition**, is `i` more than 3?, will be `True` for as long as the counter (`i`) remains less than 3, and the execution of the **function** `printf` and the **operation** `i++` will recur until the **condtion** is `False`.

It is convention to name the *iterating* **variable** `i`, for *iteration*, when programming **loop**. `j` would be the **variable** name of a second **loop**, `k` a third and so on. Should there be need for a **value** to remain **constant**, **C** has the `const` **keyword**. e.g., `const int i = 5`. Furthermore, the syntactic convention for counting is to start from 0 and *go up to* less than, `<`, your target value. Less than or equal to, `<=`, will result in the counter going up to 4 rather than 3 because counting always includes the 0 indicies, i.e., `i < 3` = 0,1,2 where `i <= 3` 0,1,2,3. Similarly, a countdown could be programmed by **valuing** `i = 3;` and executing `i--;`, `while (i > 0)`. 

    #include <stdio.h>

    int main(void)
    {
    int i = 0;
    while (i < 3)
        {
        printf("meow\n");
        i++;
        }
    }

An alternative, more elegantly designed, method of the above example would be to implement a `for` loop instead of a `while`. As you will see below the `for` **keyword** preceeds three separate **arguments**: `int i = 0;`, `i < 3;` and `i++`. The `for` loop will *recursively execute* the **function** `printf` for as long as the **condition** within brackets that succeeds it is `True`.

    #include <stdio.h>
    
    int main(void)
    {
    for (int i = 0; i < 3; i++)
        {
        printf("meow\n");
        }
    }

To programme an **infinite loop**, simply programme `while (True)` followed by whatever programming you want to *recursively execute* forever. To escape the **infinite** execution of a **loop**, enter `Ctrl C` via your **terminal**.

**Nested Loops** are **loops** within **loops**. The *contained ***loop*** is initiated when the containing ***loop*** completes a single recursion*. Commands in an **indented** line are only executed if the **condition** in the line above is `True`. `{}` and indentations mark the sections of programme that are *countained* within the greater part of the programme. In the below example each constituent section of programming in enclosed within three pairs of curly braces, i.e., `{}`, and indented. 

    int main(void)
    {
        const int n = 3;
        for (int i = 0; i < n; i++)
        {
            for (int j = 0; j < n; j++)
            {
                printf("#");
            }
            printf("\n");
        }
    }


## Command Line
- `./`: Execute file.
- `*`: An asterisk next to a filename means it is executable.
- `ls`: List files within a ***working*** **directory**.
- `mv`: Moves, or renames, a file. e.g., `mv hello hello.c` has moved hello to hello.c.
- `cp`: Copy.
- `mkdir`: Make a directory. e.g., `mkdir hello`.
- `rm`: Remove.
- `rmdir`: Remove directory.

## Operators

The mathmatical **operations** supported by your **compiler** and featured in **C**.
- `+`: Addition.
- `-`: Subraction.
- `*`: Multiplication.
- `/`: Division.
- `%`: Remainder.

## Data Types

The data types that can be stored within a **variable**. **Python** does not require you to declare the data type. **C**, however, does.

- `bool`: **Boolean** expression: `True` or `False`. X
- `char`: A single character like 'a' or '2'.
- `string`: A string of characters. X
- `int`: Integers up to a certain size, or number of **bits**.
- `long`: Integers with more **bits** to count higher than an `int`.
- `float`: A floating-point value, or real number with a decimal value.
- `double`: A floating-point value with more digits than a `float`.

Data types have specific limits, e.g., Generally, we use 32bit to represent an `int`, therefore the biggest number we have the memory to represent is 4294967296. Because we also need the capacity of our 32bit to represent negative numbers, we have to halve 4294967296 and allocate half to the negative side of the range of representation. Counting too high and running out of **bits** is when we encounter **interger overflow**. e.g., You only have 3bit but want to represent the **value** 8. Once you get to 7 (111) you **wrap around** back to 0 (000) or even to a negative number.

**C** has the `long` data type that has more (64) **bits** available to it and can therefore represent longer intergers. Likewise, **Floating-point imprecision** is the limited precision with which a number can be output due to memory contrains. A computer can only be so precise when constrained by its **bits**, so in this instance rather than **casting** our number as a `float` we should **cast** it as a `double`, which, as the name suggests, has 64bit available to it. These are real world problems a programmer must content with; even **Python** will be challenged by **floating-point imprecision**.

Type **casting** is necessary to convert one type to another, such as an `int` to a `float`, without errors, such as **truncation**, i.e., the removal of all intergers after a decimal point. 
 
## Format Codes

**C** requires format codes when printing, hence the 'f' in `printf`. These are codes which act as stopgaps for **values** that are to be deteremined elsewhere in the programme and whose inclusion is necessary in the current **argument**.
- `%c`: Stopgap for a `char`.
- `%s`: Stopgap for a `string`.
- `%i`: Stopgap for an `int`.
- `%li`: Stopgap for a `long` interger.
- `%f`: Stopgap for a `float`.
- `%.n`: Stopgap for a `float` to n decimal places.