# Week 0 

Computer science is the study of information, how it is represented and how it is processed. The application of computer science is computational thinking, i.e., problem solving.

## Binary

**Unary** uses a single entity (0) to store and represent information.
Unary 'counts' in base-1: 1^*0*, 1^*1*, 1^*2*, 1^*3* etc. 

**Binary** uses two entities (0-1) to store and represent information.
Binary 'counts' in base-2: 2^*0*, 2^*1*, 2^*2*, 2^*3* etc.

**Decimal** uses ten entities (0-9) to store and represent information.
Decimal 'counts' in base-10: 10^*0*, 10^*1*, 10^*2*, 10^*3* etc.

When working with bases you are multiplying the *product* by the *power* of *n*. You are *not* adding to the current *product* as you would in a normal: *x* * *n*, but multipying it by *n*, that is to say: *n* * *n* * *n*, rather than 3 * *n* being akin to: *n* + *n* + *n*. When working with bases the latest *product* is always double the last *product*. Therefore, *x*^0 will always be 1, not 0 because you have *not* yet started doubling. *x*^1 will always be *x*, from which point on the *product* will double sequentially. Think of *n* as the number of doubles being performed on *x*. e.g., If you were to work backwards and divide by *x* by the previous *product* you will eventually arrive at: *x* / *x* = 1. It is for this reason that in computer programming an **index** of intergers begins from 0.

## Representation

Computers represent information in **binary**, i.e., 0s and 1s - 'off' and 'on'. A **transistor** is the mechanism by which computers know if something is 'off' or 'on', it is a 'switch'. One unit of **binary**, that is a single pair of 'off' and 'on', is called a **binary digit**, i.e., a **bit**. 8 **bits** is 1 **byte**; the _unit of measure for digital information storage._ 8 **bits** = 1 **byte** = 2^8 = 256 different 'off' and 'on' permutations, ranging from 00000000 - 11111111. Computers generally use a single **byte** to represent a number, e.g., 00000101 is 5 in **binary**. To increase the number of permutations, and thus the amount of information a computer can store and represent, you can increase the number of available **bytes** by increaseng the number of **transistors**, i.e., by using more hardware. 8bit> 16bit> 32bit> 64bit etc. Computers are ostensibly millions, perhaps billions, of **transistors** being turned 'off' and 'on'. By working in **binary**, and thus **bytes**, computers are able to represent far more information than if it were to work in **unary**, and is more elegant than **decimal**.

Bytes can be used to represent pixles, images, sound frequencies etc. **ASCII** is the industry standard by which specific **binary** sequences correspond to recognisable letters, numbers, symbols, emoji etc.

![ASCII](<ascii.png>)

*RGB*, or red, green, blue, is simply a combination of three corresponding numbers that combine to create a fourth colour. Images are little more than a collection of these *RGB* numbers, and videos are a sequence of images stored together and show at a frame rate that makes the images, or frames, appear in motion.

## Abstractions & Algorithims

An **abstraction** is a *low-level* concept that you understand just in the **abstract**, like a car, without a grasp of its details. You just need to apprehend a complex concept as a *low-level* **abstraction** in order to make use of it at a *higher level* of **abstraction**, like knowing how to drive a car without understanding *how* the entire car was made and *why* it works. In the case of computer programming, you programme in *higher* languages than **binary**, which you understanding of can happily stay at a *low-level* of  **abstraction** without impeding your ability to programme sufficiently.

An **algorithim** is a computer science **abstraction**. It is not strictly necessary to know *how* an **algorithim** has solved a problem, just that its use *can* solved a problem. Problem solving can be broken down fundementally to ***input> 'Black Box'> output*** where the **algorithim** is within the, so called, 'Black Box'.

_**Abstraction** is an essential skill and concept within computer programming. Fundementally, it is the act of *simplifying* a problem in to smaller and smaller problems._

In the example below you have three **functions**. You have the `main` **function** that **calls** the **functions** `get_size` and `print_grid`. `main` is a bespoke function made by you and not a native feature of the language **C**. **Calling** the short line `get_size` **returns** the **value** `n` by executing more complex programming written elsewhere. **Calling** `print_grid` prints the grid to `n` specification by executing more complex programming written elsewhere.

Because you **abstracted** away the essential problems within the programme, the `main` **function** is short, containing only two short **functions**, while the actual workings of the other two **functions** are *implemented* elsewhere in in the programme.

    #include <cs50.h>
    #include <stdio.h>

    int get_size(void);
    void print_grid(int n);

    int main(void)
    {
        int n = get_size();
        print_grid(n);
    }

    int get_size(void)
    {
        int n;
        do
        {
            n = get_int("Size: ");
        }
        while (n < 1);
        return n;
    }

    void print_grid(int n)
    {
        for (int i = 0; i < n; i++)
        {
            for (int j = 0; j < n; j++)
            {
                printf("#");
            }
            printf("\n");
        }
    }

The lesson is to use what works if it is readily available and to not reinvent the wheel. _You should be well-aware of what solutions, like **libraries**, are at your disposal._

## Basic Programming

- **Pseudocode**: A pre-programming plan of well-defined programme behaviour for every possible scenario you might encounter when trying to engineer a solution.  **Pseudocoding** before you actually programme helps you to think through the logic of your problem in advance. 

_Your ability to create **pseudocode** is essential to your success as a programmer._

- **Curly Braces**: In **C**, `{}` syntax is used to define blocks of programming. A block can contain one or more statements. The programming within **curely braces** is treated as a single unit and is executed together.

These blocks define a *scope*, i.e., they create a context within which **variables**, **functions**, and **statements** are valid and accessible. A *scope* defines where in the programme certain elements are visible and useable. By defining different *scopes*, you can organise a clear separation between blocks of programming and prevent unintended interactions or **variable** name clashes between multiple blocks of a large programme.

- **Indentations**: **Indent** your lines of programming _four_ spaces at a time to make clear which blocks of programme are **nested** inside others. **Programming construcst** in an **indented** line only execute if the **condition** in the line above is `True`.

If you use 'tab' to **indent**, be sure that your **text editor** is configured to convert it to _four_ spaces since 'tab' renders differently in different **editors**.

    for (int i = 0; i < LIMIT; i++)
    {
        for (int j = 0; j < LIMIT; j++)
        {
            for (int k = 0; k < LIMIT; k++)
            {
                // Do something
            }
        }
    }

- **Comments**: Are useful to those seeking to understand your programming decisions and how your programme works. They can also remind you of the same when revisiting old programmes. Heading any .c and .h files should be a **comment** that summarise what your programme or particular file does.

_**Commenting** *each* interesting block of programme is *essential* and only requires a brief sentence or two._ Write **comments** that address one or both of these questions: _"What does this block do and why did I *implement* this block in this way?"_ Atop each of your **functions** except, perhaps, `main`, should be a **comment** that summarises what it does.

**Comments** are an approximation of **pseudocode** in that **commenting** in as direct terms as possible, i.e., at a *high-level*, what you want to do is the first step in programming a solution. You are **abstracting** away *low-level* complexity for a more refined vision. 

In **C**, `//` syntax is used preceeding a **comment**. Leave one space between `//` and your **comment’s** first character and capitalise it, unless it is the name of a **function**, **variable** or the like. **Comment** above the lines of programming, i.e., **in-line**, to which it applies. Keep them short, e.g., one line, and no need to write in full sentences, else it becomes illedgible. 

- **Statement**: A complete line of programming that performs a specific action. **Statements** are the building blocks of a programme, they include, **variable** **assignments**, **control flow structures**, like **loops** and **conditionals** and **function calls**. **Statements** are typically signalled by `;` syntax, which marks their termination.

- **Functions**: A **programming construct** that makes the programme 'do' something. Things that create actions. **Funcations** are **algorithims** and, by extension, **abstractions**, i.e, the working details of an **algorithim** are **abstracted** away in their *implementation*.

It does not matter *how* an **algorithim** works once it has been engineered, just that you *can* use it. All the complexity and utility of an **algorithim** can be contained and leveraged within a simple **function**, like `printf()` or `get_int()`.

- **Calling:** Execute a **function** to operate on the **arguments passed** to it.

- **Pass**: The provision of a **value**, i.e., an **argument**, to a **function** for it to operate on, once **called**.

- **Argument/Parameter**: A **value** that a **function** operates on to **return** a new **value**. **Arguments/parameters** are contained within `()` syntax without a space following the **function's** name.

In the example below when **calling** `int add` with the **arguments** `add(5, 3)`, '5' and '3' are the `arguments` **passed** to the **function**, and **assigned** to the **parameters** 'a' and 'b', which were acting as stopgaps within the **function** before it had any **values passed** to it. In terms of the 'Black Box': ***argument> function> output***.

return_type function_name(arguments);

    int add(int a, int b)
    {
        return a + b;
    }

- **Condtionals**: A 'fork in the road' where the programme is faced with a 'this or that', `True` or `False` situation; a **boolean** expression. Generally, `False` = 0 and `True` = 1 in a **boolean** expression.

- **Events**: Anything graphical or interactive that happens in a computer programme.

- **Side Effect**: A *visual* resultant of **calling** a **function**, like 'hello, world' printing to your **terminal**. In terms of the 'Black Box': ***argument> function> side effect***.