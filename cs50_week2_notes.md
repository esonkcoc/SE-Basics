# Week 2

## Compiling

`make` is not a **compiler**, it is shorthand for the automation of the **clang**, or **C** language, process. **Clang** is a **compiler** programme that could be used as a command like `make`, e.g., `clang hello`. This would compile 'hello' but not produce, known as the **assembler output** or `a.out`, a satisfactorily descriptive filename. Better to use the **command line argument (CLA)**  `clang -o hello hello.c` where `-o` means output, and to run the programme as normal by executing `./hello`. Non-native **libraries** you have imported and programmed for will not be **compiled** and trying to will cause an error. The new **command line argument** `-o hello hello.c -lcs50`, where `l` stands for link and `cs50` the **library** for inclusion, would require executing. There is no benefit to running `clang` manually other than having greater 'control'.

There are four stages to **compiling**:

1. **Preprocessing**: `#` syntax at the beginning of a line means it is a **preprocessing directive**, i.e., it is analysed initially before anything else happens. This is the case with header files, e.g., `# include <cs50.h>`, where `#` signals that `<cs50.h>` needs inclusion before anything else. `include`, like `make`, is another shorthand for the automation of a longer **functions prototype**.
2. **Compile**: After all the `#` lines have been **preprocessed** and converted in to something else, **C** is **compiled** in to **assembly code**.
3. **Assembling**: **Machine code** (0s and 1s) conversion. This only applies to the **binary** of the original *programming*, *not* the pre-made **libraries** or **functions** imported and used throughout the programme.
4. **Linking**: The **binary linking** of your progamming to all the other **binary** of the pre-made programming, e.g., **libraries** or **functions**, you have made use of.

**Function Prototype**: Header declarations that provide information about a **function's** name, **return type**, and **argument types** to the **compiler** before the actual **function** programming appears. This is necessary so that your programme can anticipate **functions** that are to come and not err when the **function's implementation** comes after it being **called**. This is a feature of **C** and not **Python**.

With all of this complexity **abstracted** away behind a simple **function** like `make`, a programmer can opperate at *higher level*.

**Decompiling**: The reverse of **compiling**. In this state, your programme will miss the clarity of style of **source code** because it has come from a state of pure functionality: **machine code**. This is a window in to how a computer only deals in the raw logic of a line of programming, where **variable** names and whether a **loop** is `for` or `while` are incidenetal to the reality of the command being executed.

## Debugging

**Debugging** allows you to step through the programme at a slower pace.

`printf` is a quick way to check what your programme is outputting; to recieve feedback. e.g., `printf("i is %i", i);` will show you what *iteration* you are currently on. Therefore, you can print whatever should be output at a given *iteration*. In this sense you can use `printf` to 'investigate' a **constructs** of your programme that interest you. It is like being able to call on the aid of a quick visualisation in to proceedings.

**Debugger**: `debug50` is the CS50 **IDE** **debugger**. When **debugging** you can make a **breakpoint** in the *gutter* of VSCode to stop the **debugger** at a specific line and to check everything prior. A panel on the left of the **text editior** will display **debug** information about the section of programme it has checked. A control panel will appear above the **text editor**: the triangle will check the programme to completeion, the curved arrow will **step over**, that is to say it will just run that line of programme *without doing a deep analysis of the underlying logic*, the downward arrow will **step in** to a line and analyse it deeply for problems if you have its **source code**, i.e., nothing pre-made.   

Vocally expressing what you are trying to do helps clarify the logic of the problem at hand; talk through things with colleagues. Don't stare at the screen for hours; walk away, try something new.

## Data Types in Memory

Data is stored in **memory** *contigiously*: top to bottom, left to right. Each **byte** of data is stored one after another, they can *not* be stored in isolation, in a remote area of **memory**. A computer has finite **memory** and each data type requires a certain amount of system resources:
- `bool`: 1 byte
- `char`: 1 byte
- `string`: ? bytes (the number of **bytes** allocate to a `string` varies because a `string` is not a consistent length and each constituent `char` has 1 **byte** of **memory**)
- `int`: 4 bytes
- `long`: 8 bytes
- `float`: 4 bytes
- `double`: 8 bytes

![1 byte stored in memory](<1byte_in_memory.png>)
*1 byte stored in memory*

![4 bytes stored in memory](<4bytes_in_memory.png>)
*4 bytes stored in memory*

- **Arrays**: A collection of **indexed values**, each individually accessible. Rather than having multiple **variables** for a collection of **values**, they can all be stored within a single **array** the size of your choosing and individually manipulated by knowing where within the **array** the specific **value** is located, i.e., **indexed**. **Arrays** are a way of storing data back-to-back in **memory** such that this data is easily accessible. e.g., `int score [3]` is a way of telling the **compiler** to provide three back-to-back places in **memory** of `int` size **bytes** to store three 'scores'.

![12 bytes stored in memory](<12bytes_in_memory.png>)
*12 bytes stored in memory*

As well as being containers for **indexed values**, **arrays** can also be **passed** as **arguments**. e.g., `float average(int array [])`. In this example 'array' is *not* a **keyword** and could have been any **variable** name, what *is* key however is `[]` syntax which signals the creation of an as yet empty container which will  be filled with a collection of **return values** from elsewhere in the programme.

By definition, an **array** always contains an `int` data type because whether you are storing `char` or `string` they are all ultimately understood by the programme by their **ASCII value** which is an interger. Nevertheless, in practice we must always cast **arrays** as the appropriate data type.

- **Characters**: Inverted commas denote the contained **value** is a `char` data type, while quotation marks denote the contained **value** is a `string` data type. At a *lower-level*, all recognisable characters, i.e., letters, numbers and symbols, are **variables** for a corresponding `int` **ASCII value** which, in turn, is a **variable** for a sequence of **bits** (0s and 1s), i.e., **binary**. It is this sequence of 8 **bits** that make up the **bytes** which the programme is fundementally dealing in.

When programming, we *must* think in these terms: *when accessing the **memory** location where a character is stored, it is ultimately the sequence of **bits** that corresponds to the character's specific **ASCII value** that is being retrieved, **operated** on and transformed, *not* the *higher-level* **abstraction** itself,* i.e., letters, numbers and symbols. Those **abstractions** are only the recognisable 'faces' of **binary**. Storing information in **memory** as a sequence of **bits** is not a 'choice' but fundemental computational architecture.

Considering the above, when we perform an **operation** like `bits[i] = c % 2;` what we are doing is storing the modulus **return value** at location `i` of the 'bits' **array**. The **return value**, i.e., the remainder following the division of the character's corresponding `int` **ASCII value** by 2, is either 0 or 1. In effect, this operation is extracting the character's **binary** one **bit** at a time and storing them in reverse sequence in 'bits'. Given the `char` data type occupies 1 **byte** of **memory** and there are 8 **bits** in a **byte**, 'extraction' and storage will continue until all 8 **bits** of the character's **binary** are retrieved. The **bit** up for 'extraction' and its storage location, or **index**, in the **array** is whatever *iteration* the **loop** is on. When in correct sequence, this **array** of **bits** represents information we recognise as the original *high-level* character, i.e.,a letter, number or symbol.

Furthermore, you can now imagine how you might use a character's `int` **ASCII value** to programme the converstion of a user input from upper to lowercase simply by appropriately **operating** on said **value**.

- **String**s: **Arrays** of characters, or an **array** of **variables** of data type `char`. The individual **values** located throughtout a string can be accessed via their specfic **index**. In **memory**, strings are stored as '*n*+1' where *n* represents the total length of the string and 1 the '\0' character (0 = nul in **ASCII**), which acts as a *delimitor* between separate strings. The programme knows a string has ended when it encounters '\0'. A string, therefore, always takes up one more **byte** than the programmer entered.

![A string in memory](<string_in_memory.png>)
*A string stored in memory*


![Characters in memory](<chars_in_memory.png>)
*Characters in memory*


In **C**, the length of an **array** can *not* be discovered *dynamically* but a string's can because of the '/0' character. Because string use is so common it has some 'priviledged' characteristics and a whole **library** (`string.h`) dedicated to its most useful **functions**. Likewise characters have their own **library** of most useful **functions** (`ctype.h`).

An **array** can contain two seperate strings that can have their individual character **values** accessed. e.g., `string array [2]` you have cast your **array**-contained data type as a `string`, named your **variable** 'array', signalled we are creating an **array** with `[]` and set the number of **arrays** to 2. `array [0][0], [0][1], [0][2]` evoke the **variable** 'array' and access the first `string` [0] and its first `char` [0], the first `string` [0] and its second `char` [1], the first `string` [0] and its third `char` [2].

![2 strings in memory](<2strings_in_memory.png>)
*2 strings in memory*


- **Command Line Arguments**: Anything after a **CLI** command. e.g., `cd ...` or `clang ...`. **CLA's** let you express your intention all at once. So far, the two 'official' formats for defining a `main` **function** are `(void)`, i.e. no **CLA**, and `(int argc, string argv[])`, i.e, a **CLA**. Here, `argc` represents 'CLA count' and `argv` the length of the list of words, or **array** of strings, entered at the **prompt**. We need `argc` because **arrays** do not keep track of their length and thus must have a count initilised. Individual strings can keep track of their length but an **array** of strings can not.

- **Exit Status**: Whenever your `main` **function** exits it **returns** a 'hidden' interger which can be revealed through some advanced programming. Typically, they indicate errors, and error codes, like 404, are examples of **exit statuses**. After exiting without error, a status of 0 is output. Often, when an error occurs that results in the programme ending, a status of 1 is output. `main` is always cast as an `int` and always **returns** 0 although it is not displayed. Executing the command `echo$` will display the **exit status** in your **CLI**.

- **Cryptography**: The science of **encrypting** information by moving it through an **algorithim** and turning it in to a cipher, there by **encrypting** it.

One who knows the particular **algorithim** and input used to **encrypt** information can also use them to **decrypt** it. In terms of the 'Black Box': ***plain text + key> cipher> cipher text***. You can **pass** multiple **arguments** to a **function** so you can also **pass** a 'key' with the message. The 'key' dictates by how much the cipher moves the letters along, in what is known as a 'caeser cipher'. Add a **value**, i.e., the 'key', to each letter and output the new **value**. To **decrypt** the cipher, apply this method in reverse. In terms of the 'Black Box': ***reverse -1 cipher> cipher> decrypted text***.
