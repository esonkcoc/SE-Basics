# Week 0 

Computer science is the study of information, how it is represented and processed. The application of computer science is computational thinking, i.e., problem solving.

## Binary

**Unary** is using a single entity (0) to store and represent information.
Unary 'counts' in base-1: 1^*0*, 1^*1*, 1^*2*, 1^*3* etc. 

**Binary** is using two entities (0-1) to store and represent information.
Binary 'counts' in base-2: 2^*0*, 2^*1*, 2^*2*, 2^*3* etc.

**Decimal** is using ten entities (0-9) to store and represent information.
Decimal 'counts' in base-10: 10^*0*, 10^*1*, 10^*2*, 10^*3* etc.

When working with bases you are multiplying them by the **power** of ***n***. You are not adding as you would in a normal *x* * *n*, but multipying by *n*, that is to say *n* * *n* * *n*, rather than 3 * *n*. When working with bases the output is always double the last output. Therefore, *x*^0 will always be 1, not 0 because you have *not* yet started doubling. *x*^1 will always be *x*, from which point on *x* will double sequentially. Think of *n* as the number of doubles being performed on *x*. e.g., if you were to work backwards and divide by the previous result you will eventually arrive at 2/2=1. It is also for this reason that in computer programming an index of intergers begins from 0. 

## Representation

Computers represent information in **binary**, i.e., 0s and 1s, or 'off' and 'on'. A **transistor** is the mechanism by which computers know if something is 'off' or 'on', it is, so to speak, a 'switch'. One unit of **binary**, that is a single pair of 'off' and 'on', is called a **binary digit**, i.e., a **bit**. Eight **bits** is one **byte**; the unit of measure for digital information storage. Eight **bits** = one **byte** = 2^8 = 256 different 'off' and 'on' permutations, ranging from 00000000 - 11111111. Computers generally use a single **byte** to represent a number, e.g., 00000101 is 5 in **binary**. To increase the number of permutations, and thus the amount of information a computer can store and represent, you can increase the number of available **bytes** by increaseng the number of **transistors**, i.e., by using more hardware. 8bit> 16bit> 32bit> 64bit etc. Computers are ostensibly millions, perhaps billions, of **transistors** being turned 'off' and 'on'. By working in **binary**, and thus **bytes**, computers are able to represent far more information than if it were to work in unary, and is more elegant than decimal.

Bytes can be used to represent pixles, images, sound frequencies etc. **ASCII** is the industry standard by which specific combinations of **binary** correspond to specific letters, symbols, emoji etc.

![ASCII](<cs50Week0Slide93-1.png>)

**RGB**, or red, green, blue, is simply a combination of three corresponding numbers that combine to create a fourth colour. Images are little more than a collection of these **RGB** numbers, and videos are a sequence of images stored together and show at a frame rate that makes the images, or frames, appear in motion.

## Abstractions & Algorithims

An **abstraction** is a *low-level* concept that you understand just in the abstract, such as a car, without a grasp of its details. You just need to apprehend a complex concept as an **abstraction** in order to make use of it at a *higher level* of **abstraction**, like knowing how to drive a car without understanding how the entire car was made and why it works. In the case of computer programming, we programme in *higher* languages than **binary**, which our understanding of can happily stay as a *low-level* **abstraction** without impeding our ability to programme sufficiently.

An **algorithim** is a computer science **abstraction**. It is not strictly necessary to know *how* an **algorithim** has solved a problem, just that its deployment *can* solved a problem. Problem solving can be broken down fundementally to ***input> 'Black Box'> output*** where the **algorithim** is within the, so called, 'Black Box'.

_**Abstraction** is an essential skill and concept within computer programming. Fundementally, it is the act of *simplifying* a problem in to smaller and smaller problems._

In the below example we have three **functions**. We have the `main` **function** that calls the **functions** `get_size` and `print_grid`. `main` is a bespoke function made by you; it is not a native feature of the language. `get_size` includes the complex programming to accomplish the task of getting the grid's size. **Calling** `print_grid` prints the grid to specification. Because we **abstracted** away the essential problems within our programme, the `main` **function** is very short, while the actual workings of the other two **functions** are dealth with elsewhere in in the programme.

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

## Basic Programming

- **Pseudocode**: A pre-programming plan of well-defined programme behaviour for every possible scenario you might encounter when trying to engineer a solution. _Your ability to create **pseudocode** is essential to your success in programming_. **Pseudocoding** before you actually programme helps you to think through the logic of your problem in advance. 

- **Comments**: Can be used as an approximation of **pseudocode** in that **commenting** at a *high-level* what you want to do is itself the first step in programming. You are **abstracting** away *low-level* complexity for a highly refined understanding. _**Commenting** *each* block of programme is *essential* and only requires a brief sentence or two._ It is also useful to those seeking to understand your programming decisions and how your programme works. In **C**, `//` is the syntax used that preceeds your **comment**.

- **Functions**: A category of command that makes the programme 'do' something. Things that create actions. **Funcations** are **algorithims** and, by extension, **abstractions**, that is, the working details of an **algorithim** are an abstraction. It doesn't matter *how* an **algorithim** works once it has been built, just that you can implement it. All the complexity and utility of an **algorithim** can be encapsulated and excercised by deploying a simple **function**, like `printf()` or `get_int()`.

- **Condtionals**: A 'fork in the road' where the programme is faced with a 'this or that', `True` or `False` situation; a **boolean** expression. Generally, `False` = 0 and `True` = 1 in a **boolean** expression.

- **Indentations**: Commands in an **indented** line are only executed if the **condition** in the line above is `True`.

- **Events**: Anything graphical or interactive that happens in a computer programme.

- **Argument/Parameter**: An input to a **function** that changes its behaviour in some way. In terms of the 'Black Box': ***argument> function> output***.

- **Side Effect**: A *visual* resultant of **calling** a **function**, like 'hello, world' printing to your **terminal**. In terms of the 'Black Box': ***argument> function> side effect***.