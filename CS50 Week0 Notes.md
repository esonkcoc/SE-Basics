# Week 0 

Computer science is the study of information, how it is represented and processed. The application of computer science is computational thinking, i.e., problem solving.

##Binary

**Unary** is using a single entity (0) to represent information.
Unary works in base-1: 1^*0*, 1^*1*, 1^*2*, 1^*3* etc. 

**Binary** is using two entities (0-1) to represent information.
Binary works in base-2: 2^*0*, 2^*1*, 2^*2*, 2^*3* etc.

**Decimal** is using ten entities (0-9) to represent information.
Decimal works in base-10: 10^*0*, 10^*1*, 10^*2*, 10^*3* etc.

When working with bases you are multiplying by the **power** of ***n***. You are not adding as you would in a normal *x* * *n*, but multipying by *n*, that is to say *n* * *n* * *n*, rather than 3 * *n*. When working with bases the output is always double the last output. Therefore, *x*^0 will always be 1, not 0 because you have *not* yet started doubling. *x*^1 will always be *x*, from which point on *x* will double sequentially. Think of *n* as the number of doubles being performed on *x*. e.g., if you were to work backwards and divide by the previous result you will eventually arrive at 2/2=1. It is also for this reason that in computer programming an index will always begin from 0. 

##Reresentation

Computers represent information in **binary**, i.e., 0s and 1s, or 'off' and 'on'. A **transistor** is the mechanism by which computers know if something is 'off' or 'on', it is, so to speak, a 'switch'. One unit of binary, that is a single pair of 'off' and 'on', is called a **binary digit**, i.e., a **bit**. Eight **bits** is one **byte**; the unit of measure for digital information storage. Eight **bits** = one **byte** = 2^8 = 256 different 'off' and 'on' permutations, ranging from 00000000 - 11111111. To increase the number of permutations, and thus the amount of information a computer can store and represent, you can increase the number of available **bytes** by increaseng the number of **transistors**, i.e., by using more hardware. 8bit> 16bit> 32bit> 64bit etc. By working in binary, and thus **bytes**, computers are able to represent far more information than if it were to work in unary, and is more elegant than decimal. Bytes can be used to represent pixles, images, sound frequencies etc.

##Abstractions & Algorithims

An **abstraction** is a *low-level* concept that you understand just in the abstract, such as a car, without a grasp of its details. You just need to apprehend a complex concept as an **abstraction** in order to make use of it at a *higher level* of abstraction, such as knowing how to drive a car without understanding in detail how the entire car was made and works. In the case of computer programming, we programme in *higher* languages than **binary**, which our understanding of can happily stay as a *low-level* **abstraction** without impeding our ability to programme sufficiently.

An **algorithim** is a computer science **abstraction**. It is not strictly necessary to know how an **algorithim** has solved a problem, just that its deployment can. Problem solving can be broken down fundementally to ***input> 'Black Box'> output*** where the **algorithim** is the, so called, 'Black Box'.

##Basic Programming

- **Pseudocode**: A pre-programming plan of well-defined programme behaviour for every possible scenario you might encounter when trying to engineer a solution.
- **Functions**: A 'class' of commands that makes the programme 'do' something. Things that create actions. **Funcations** are **algorithims** and, by extension, **abstractions**, that is, the working details of an **algorithim** are an abstraction. It doesn't matter *how* an **algorithim** works once it has been built, just that you can implement it.
- **Condtionals**: A 'fork in the road' where the programme is faced with a 'this or that', `True` or `False` situation; a **boolean** expression.
- **Indentations**: Commands in an **indented** line are only executed if the **condition** in the line above is `True`.
- **Events**: Anything graphical or interactive that happens in a computer programme.
- **Argument/Parameter**: An input to a function that changes its behaviour in some way. In terms of the 'Black Box': ***argument> algorithim> output***.
- **Side Effect**: The result of **calling** a **function**. In terms of the 'Black Box': ***argument> algorithim> side effect***.

Go in with a plan. Be prepared for things to take much longer than you think.
Don't fret the great, initial mental energy require to get your head around a new concept or tool; you will build momentum. To help build momentum, do not keep banging your head against a wall. Take the *initiative* to research soluions online and via Chat GPT but never implement them without understaning why they work first.
Be methodical, solve one problem at a time. Keep, dividing, i.e., breaking down, problems until there is no 'problem' left to solve.
Solutions can be found in both syntax errors and control flow; check both.
Try things, try solutions. Do the simple things first.
Don't do everything all at once. Take your time; baby steps. Write, test, write, test, write etc.
You try harder to solve 'good' questions, i.e., ones that interest you.
Ideas will be more familiar than you yet realise because they are being presented in an unfamiliar light.

