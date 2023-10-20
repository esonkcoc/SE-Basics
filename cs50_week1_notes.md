# Week 1

## Machine Code & Source Code

**Source code** is any computer programme, written in any programming language by a programmer, intelligable to humans. **Machine code** is the converted form of **source code**, which is intelligable to a computer as **binary**, but unintelligable to humans. **Source code** is transformed in to **machine code** by a **compiler**. In this instance, you are using VSCode to compile your programme. VSCode is a **source code**, or **text**, **editor** that features **debugging**, syntax highlighting and **compiling**, amongst other functions. Although it is not strictly an **Intergrated Development Environment (IDE)**, i.e., a software with greater native functionality, VSCode's many extensions bring it close.

## Interfaces

Your **terminal** provides a **command line interface (CLI)** within which you can command the computer to execute certain actions. Users and computers can also interact via a **graphical user interface (GUI)**, which consists of icons, like on a desktop or smartphone screen. If nothing appears in your **CLI** after you **return** a command to execute, it is normally a good sign that what you wanted has happened.

## Design and Style

_What constitutes 'good' programming? That which is fast, maintainable and elegantly communicates your solution. i.e., That which is correct, well-designed and well-styled._ If there is a lot of _'copy & paste' programming in your programme it is a sign of bad design_.

Be alert to oppertunities to **abstract** away the *low-level* complexity of your **algorithims** in favour of the elegance of a *high-level*, bespoke **function**. 
 
Do not 'hard code' numbers. No 'magic' numbers. Programme flexibility in to your programme by declareing a number as a **variable** so it can easily be changed throught the programme by altering it once in a single location. Alternativley, should there be need for a **value** to remain constant throughout your programme, **C** has the **keyword** `const`, the naming convention of which is to make uppercase. e.g., `const int MAGIC_NUMBER = 5`. 

Convention is to *not* capitalise any filenames you create.

*Never* repeat lines of programming unnecessarily if a **loop** would better serve.

## C

- `/n`: An **escape sequence** which programmes a line break in to the output. Its inclusion will move the **CLI** cursor to a new line once your programme has executed, keeping everything visually tidy. Its inclusion is convention.

- **Libraries**: Collections of additional functions a programme might need to implement but that are not natively featured within the language, possiblity due to resource constrains and impracticality. To find out what functionality a language features natively and what **libraries** are available, *always* refer to the **documentation**. To import a **library** to **C**, write the **preprocessing directive** `# include <library>` at the head of your programme.

Any such **libraries** that header your programme should be listed in alphabetical order. This makes them easier to see at a glance, particularly in a long list.

Including a file will import much unseen programming you do not need which is why a programme as simple as 'hello, world' contains so many 0s and 1s.

- **Return Value**: A **value** resultant of **calling** a **function** that can be *reused* within the programme. Where as a **side effect** is an 'inert', *visual* resultant, like 'hello, world' printing to your **terminal**. In terms of the 'Black Box': ***argument> function> return value***.

A `return` **statement** indicates the end of a **function** and specifies the **value** the **function** should **return** to the **caller**. **Functions** can have multiple `return` **statements**, each **returning** a different **value** based on specific conditions or branches within the **function**. The appropriate `return` **statement** is executed depending on the flow of the programme. Once the **value** is **returned**, the programme will continue executing from the point where the **function** was **called**. A `return` **statement** allows you to control the flow of your programme. e.g., you can use `return` to exit a **function** early if a **condition** is met, avoiding unnecessary computation.

In some cases, **functions return status codes** to indicate whether they executed successfully or encountered an error.

- **Compiling** and **Running**: In **C**, your programme must be **compiled** before it can run and *must* be without errors for it to **compile**. First, create a file by executing the command `code new_prog.c`. This is where your **source code** will reside. `code` is a command specific to VSCode. Next, execute the command `make new_prog`, where `make` **compiles** by searching for a .c file of the given name to transform in to **machine code**. Finally, the executable file `new_prog` will be created and is where the computer-intelligable **machine code** resides. To run `new_prog` execute the command `./new_prog`. `./` is the universal command to run any file in your ***working*** **directory**.

- **Variables**: Are 'containers' for **values**. They only exists inside the *scope* of the most recent `{}` and therefore must be declared when and where you actually need them, and not too late. *Scope* your variables as tightly as possible. e.g., if `i` is only needed for the sake of a **loop**, declare `i` within the **loop** itself, not at the head of the programme.

    for (int i = 0; i < LIMIT; i++)
        {
        printf("%i\n", i);
        }

**Variable** names must be as representative of the **value** as possible. If *summing* some **values**, name your **variable** `sum`. If your **variable’s** name warrants two words, e.g., `is_ready`, put an underscore between them, a convention popular in **C** though less so in other languages.

A **variable's value** can change depending on **conditions** being met elsewhere in the programme, such as a user input or **boolean** expression. In the example below you see the variable `answer` is **assigned** by syntax `=` to whatever **value** the **function** `get_string` has **returned** to it by a user prompted with the **input string** "What's your name? ". At the beginning of the **statement**, `answer`'s data type is declared `string`. This signals to the programme that the **return value** must be a sequences of characters, i.e., `string`. In **C**, once a **variable** has had its data type initially signalled, the programme does not require it to be declared again.
   
    #include <cs50.h>
    #include <stdio.h>

    int main(void)
    {
        string answer = get_string("What's your name? ");
        printf("hello, %s\n", answer);
    }

- **`printf`**: A **function** that, having been **passed** an **argument** and **called**, outputs a **side effect**. In the example above **C** requires `%s` syntax, i.e., **format code** as a stopgap for the user-input **value assigned** to the `answer` **variable**. `answer` is subsequent `,` and outside quotation marks, syntax which denotes the `string` data type. Finally, like `get_string`, the **statement** is terminated by  `;` syntax.

- **Conditionals**: In the example below you see the **conditional keywords** `if` and `else` take account of all potential permutations of the preceeding **function statements**. Furthermore, there is a single space after **conditionals** and before the parentheses which was not present when programming **functions**, like `printf()`, `get_int()` and `get_string()`.

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

- **Loops**: Are a **programming construct** that, under certains **conditions**, *continually execute* sections of programming. They are useful when certain **conditions** needs to be under continual check, like the validity of a user input. **Loops** also make your programme tider than a succession of 'copy & paste' programming that accounts for every concieveable **condition**.

In the example below the **variable** `i` as been **assigned** the **value** 0, which will increase by 1 after every **loop** thanks to the **operation** `i++`. Effectively, `i` is a counter. The **keyword** `while` signals that the succeeding programming is under continual check, i.e., to **loop** under a certain **condition**. How the programme will execute on the next *iteration* of the `while` **loop** depends on if the **condition** is `True` or `False`; a **boolean** expression.

The **condition** (i < 3) will be `True` for as long as `i` remains less than 3, and the execution of the **function** `printf` and the **operation** `i++` will repeat with each *iteration* of the **loop** until the **condtion** is `false`.

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

The syntactic convention for counting is to start from 0 and *go up to less than*, `<`, your target value. Less than or equal to, `<=`, will result in the counter going up to 4 rather than 3 because counting always includes the 0 **index**. i.e., `i < 3` = 0, 1, 2 where `i <= 3` 0, 1, 2, 3. Similarly, a countdown could be programmed by **valuing** `i = 3;` and executing the **operation** `i--;` under the **condition** `while (i > 0)`.

It is convention to name the *iterating* **variable** `i` when programming **loop**, `j` in a second **loop** and `k` a third. If you need more than three **variables** for *iterations*, it would be wise to rethink your design. It is fine to use names like `i`, `j`, and `k` for *iterations* but most other **variables** should be better representativley named.

An alternative, more elegantly designed, method of the example above would be to implement a `for` **loop** instead. In the example below the `for` **keyword** preceeds three separate **constructs**: `int i = 0;`, `i < 3;` and `i++`. These constructs represent the *initialisaton* of a counter **variable**: a control, a **conditional statement**: **boolean** expression, an *interation* **operation**: increments the counter **variable**. The `for` **loop** will *continually execute* the `printf` **function**, as long as the **conditions** that succeed it are `True`.

    #include <stdio.h>
    
    int main(void)
    {
    for (int i = 0; i < 3; i++)
        {
        printf("meow\n");
        }
    }

To programme an **infinite loop**, simply programme `while (True)` followed by whatever programming you want to *continually execute* forever. To escape the **infinite** execution of a **loop**, enter `Ctrl C` via your **CLI**.

**Nested Loops** are **loops** within **loops**. The *contained ***loop*** is initiated when the containing ***loop*** completes a single iteration*. Commands in an **indented** line are only executed if the **condition** in the line above is `True`. `{}` syntax and **indentations** mark the sections of programme that are *countained* within the greater part of the programme. In the example below each constituent section of programming in contined within three pairs of **curly braces** and **indented**. 

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
- `mv`: Moves or renames a file. e.g., `mv hello hello.c` has moved hello to hello.c.
- `cp`: Copy.
- `mkdir`: Make a directory. e.g., `mkdir hello`.
- `rm`: Remove file.
- `rmdir`: Remove directory.

## Operators

The mathmatical **operations** supported by your **compiler** and featured in **C**.
- `+`: Addition.
- `-`: Subraction.
- `*`: Multiplication.
- `/`: Division.
- `%`: Modulus.

## Data Types

The data types that can be stored within a **variable**. **Python** does not require you to declare the data type. **C**, however, does.

- `bool`: **Boolean** expression: `True` or `False`.
- `char`: A single character, e.g., 'a' or '2'.
- `string`: A string of characters.
- `int`: Integers up to a certain size, or number of **bits**.
- `long`: Integers with more **bits** to count higher than an `int`.
- `float`: A floating-point value, or real number with a decimal value.
- `double`: A floating-point value with more digits than a `float`.

Data types have specific limits, e.g., generally, _we use 32bit to represent an `int`,_ therefore the biggest number you have the **memory** to represent is 4294967296. Because you also need the capacity of your 32bit to represent negative numbers, you have to halve 4294967296 and allocate half to the negative side of the range of representation. Counting too high and running out of **bits** is when you encounter **interger overflow**. e.g., You only have 3bit but want to represent the **value** 8. Once you get to 7 (111) you **wrap around** back to 0 (000) or even to a negative number, instead of creating a fourth **bit** (1000 = `int` 8) from nothing. When working with **binary** you may need to prepend leading 0s to make sure the **binary** is of the desired length. i.e., 8bit represents 4 as 00000100.

**C** has the `long` data type that has more (64) **bits** available to it and can, therefore, represent longer intergers. Likewise, **Floating-point imprecision** is the limited precision with which a number can be output due to **memory** contrains. A computer can only be so precise when constrained by its **bits**, so in this instance rather than **casting** your number as a `float` you should **cast** it as a `double` which, as the name suggests, has 64bit available to it. These are real world problems a programmer must contend with; even **Python** will be challenged by **floating-point imprecision**.

Type **casting** is necessary to convert one type to another, such as an `int` to a `float`, without errors, such as **truncation**, i.e., the removal of all intergers after a decimal point. An `int` can quickly take form of a `float` by appending .0 to it. e.g., 5 becomes 5.0. 
 
## Format Codes

**C** requires format codes when printing, hence the 'f' in `printf`. These are codes which act as stopgaps for **values** that are to be deteremined elsewhere in the programme and whose inclusion is necessary to **calling** a **function**.
- `%c`: Stopgap for a `char`.
- `%s`: Stopgap for a `string`.
- `%i`: Stopgap for an `int`.
- `%li`: Stopgap for a `long` interger.
- `%f`: Stopgap for a `float`.
- `%.n`: Stopgap for a `float` to n decimal places.