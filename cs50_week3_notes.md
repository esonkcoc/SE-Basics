# Week 3

## Algorithms

In terms of **memory**, think of the process of finding a specific number in an **array** like opening each locker in a row until you find the number. The computer does not just 'know' or have instant access to everything; it requires a process of discovery. This process is an **algorithm**. **Linear** and **binary** are two such search **algorithms**.

- **Linear**: This searches every value individually and can be very tedious if the values are not sorted. Even if they were sorted, a **linear** search would take more time than other search **algorithms**. As show below, a **linear** search can really be thought of as just a **for loop** of the length of an **array**:

    #include <cs50.h>
    #include <stdio.h>

    int main(void)
    {
        // An array of integers
        int numbers[] = {20, 500, 10, 5, 100, 1, 50};

        // Search for number
        int n = get_int("Number: ");
        for (int i = 0; i < 7; i++)
        {
            if (numbers[i] == n)
            {
                printf("Found\n");
                return 0;
            }
        }
        printf("Not found\n");
        return 1;
    }

If you want to search for a string within an **array**, your programme would require modification as such:

    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>

    int main(void)
    {
        // An array of strings
        string strings[] = {"battleship", "boot", "cannon", "iron", "thimble", "top hat"};

        // Search for string
        string s = get_string("String: ");
        for (int i = 0; i < 6; i++)
        {
            if (strcmp(strings[i], s) == 0)
            {
                printf("Found\n");
                return 0;
            }
        }
        printf("Not found\n");
        return 1;
    }

The fundemental difference is that `if (numbers[i] == n)` has been replace by `if (strcmp(strings[i], s) == 0)` because you can not compare strings in **C** without the `strcmp` **function** from the the `string.h` **library**. If the **return value** after **passing** your **arguments** to `strcmp` is 0, the strings under comparison are equal. Also, we have lowered the number of **loop** iterations from 7 to 6 because we have less values to check. Had this been left as was, we would have encountered a **segmentation fault**, that is to say you 'touched' **memory** beyond the bounds. Furthermore and not specific to search **algorithms**, it is good practice to write `return *n*` at the end of a section of programming or **loop**, to inform the programme to exit and if a task has been performed successfully via an error code. Had `return` not been included the **loop** would not have broken at the appropriate place.

- **Binary**: This searches from the middle and again from the middle of either the left or right side of the previous mid-point, making the range of values under search progressivley smaller. This process **recurs** until you find your value. To **binarly** search, the values must be ordered. This method of searching is faster than **linearly**.

## Running Time

One way we judge an **algorithm's** efficiency is with **Big *O*** notation, that is the broad sense of time it takes to complete a problem at scale; its **running time**. Minor **running time** differences are negligable when considerably scaled up, so much so that an **algorithm** at the **upper bound** of **running time** may as well be another **algorithm** also near the **upper bound** when judging by the shape of line it makes on a large scale graph.


![Big O graph](<big_o_graph.png>)

*Big O graph*


- *O*(*n*2)        | Slowest 
- *O*(*n* log *n*) |
- *O*(*n*)         |              **Linear** search: Always *n* steps for the **algorithm** to perform.
- *O*(log *n*)     |              **Binary** search*:
- *O*(1)           V Fastest      One fixed step, no matter how large the value *n*.

Above is the generally accepted range of worst-case scenario **algorithm running time** speeds, as expressing in **Big *O*** notation. The **upper bound** is where the slowest **algorithms** are, the **lower bound** the fastest. Collectively, however, they all represent an **algorithm's** potential most **upper running time bound**, or worst-case efficiency, of an **algorithm**. Below is the same concept but representing an **algorithm's** potental **lowest running time bound**, known as **Omega**.

- &Omega;(*n*2)        | Slowest
- &Omega;(*n* log *n*) |
- &Omega;(*n*)         |
- &Omega;(log *n*)     |
- &Omega;(1)           V Fastest      

Both **linear** and **binary** search algorithms potentially have a **lower running time bound** of &Omega;(1) if by chance the value they were searching for were first in its **array**.

Finally, should an **algorithm's upper** and **lower running time bound** be identical for ***O*** and &Omega;, it can be said to have an efficiency of **Theta**(*order*). i.e., No matter what, the **algorithm** will always take the same number of steps to complete.

- &Theta;(*n*2)        | Slowest
- &Theta;(*n* log *n*) |
- &Theta;(*n*)         |
- &Theta;(log *n*)     |
- &Theta;(1)           V Fastest

## Data Structures

Think of **arrays** as a lightweight **data structure**. Via `struct`, **C** allows you to construct your own data types out of 'primitive' constituents that allow us to make a bespoke type for specific needs. e.g., To combine a name value and number value in one data type called `person`.

    #include <cs50.h>
    #include <stdio.h>
    #include <string.h>

    typedef struct
    {
        string name;
        string number;
    }
    person;

    int main(void)
    {
        person people[2];

        people[0].name = "Carter";
        people[0].number = "+1-617-495-1000";

        people[1].name = "David";
        people[1].number = "+1-949-468-2750";

        // Search for name
        string name = get_string("Name: ");
        for (int i = 0; i < 2; i++)
        {
            if (strcmp(people[i].name, name) == 0)
            {
                printf("Found %s\n", people[i].number);
                return 0;
            }
        }
        printf("Not found\n");
        return 1;
    }

The programme begins with`typedef struct` where a new data type called `person` is defined. Inside `person` is a string called `name` and a string called `number`. In the main **function**, begin by creating an **array** called `people` that is of the `person` data type and of size 2. You then update the names and  numbers of the two people in our `people` array. Most importantly, notice how `.` syntax, like people[0].name, allows us to access the person at the 0 index and assign that individual a name.

## Sorting

When an **array** is sorted it is far less intesive for a computer to find a specific value. Like searching, there are a range of sorting **algorithms**.

- **Selection** sort iterates through the *unsorted* portions of a list, selecting the smallest element each time and moving it to its correct location. The **pseudocode** for **selection** sort is:

    For i from 0 to n–1
        Find smallest number between numbers[i] and numbers[n-1]
        Swap smallest number with numbers[i]

Representing this mathematically, where *n* represents the number of cases, it could be said that **selection** sort can be analysed as:

  (*n*-1)+(*n*-2)+(*n*-3)+ ... + 1

or, more simply, `*n*2/2 - *n*/2`. Considering that mathematical analysis, *n*2 is really the most influential factor in determining the efficiency of this **algorithm**. Therefore, **selection** sort is considered to be of the order of *O*(*n*2) in the worst case where all values are unsorted. Even when all values are sorted, it will take the same number of steps. Therefore, the best case can be noted as &Omega;(*n*2). Since both the **upper bound** and **lower bound** cases are the same, the efficiency of this **algorithm** as a whole can be regarded as &Theta;(*n*2). 

- **Bubble** sort compares pairs of adjacent values one at a time and swaps them if they are in the incorrect order. This continues until the list is sorted, once the largest values have 'bubbled' up to the top, so to speak. The **algorithm** will only 'look' at pairs that remain unsorted once it know which have been sorted. The **pseudocode** for **bubble** sort is:

    Repeat n-1 times
    For i from 0 to n–2
        If numbers[i] and numbers[i+1] out of order
            Swap them

Analysing **bubble** sort, the worst case is *O*(*n*2), while the best case is &Omega;(*n*). 

- **Merge** sort **recursively** divides an **array** in two repeatedly and then **merges** the smaller **arrays** back in to a larger, correctly ordered, one. The **pseudocode** for **merge** sort is:

    If only one number
        Quit
    Else
        Sort left half of number
        Sort right half of number
        Merge sorted halves

**Merge** sort is a very efficient sort **algorithm** with a worst case of *O*(*n* log *n*). The best case is still &Omega;(*n* log *n*) because the **algorithm** still must visit each place in the list. Therefore, **merge** sort is also &Theta;(*n* log *n*) since the best case and worst case are the same.

## Recursion

**Recursion** is a concept within programming where a **function calls** itself. In the example below, we are calling `search` on smaller and smaller iterations of this problem:

    If no doors
        Return false
    If number behind middle door
        Return true
    Else if number < middle door
        Search left half
    Else if number > middle door
        Search right half

In the example below, the `draw` **function calls** itself. Also, the programme may get caught in an **infinite loop** because there is nothing telling it to break, i.e., no case where the programme is done. To break from this **loop** return `ctrl-c`.

    #include <cs50.h>
    #include <stdio.h>

    void draw(int n);

    int main(void)
    {
        draw(1);
    }

    void draw(int n)
    {
        for (int i = 0; i < n; i++)
        {
            printf("#");
        }
        printf("\n");

        draw(n + 1);
    }

In the example below, the **base case** will ensure the programme does not run forever. The line `if (n <= 0)` terminates the **recursion** because the problem has been solved. Every time `draw` **calls** itself, it **calls** itself by `n-1`. At some point, `n-1` will equal 0, resulting in the `draw` **function** returning and the programme will end.

#include <cs50.h>
#include <stdio.h>

void draw(int n);

int main(void)
{
    // Get height of pyramid
    int height = get_int("Height: ");

    // Draw pyramid
    draw(height);
}

void draw(int n)
{
    // If nothing to draw
    if (n <= 0)
    {
        return;
    }

    // Draw pyramid of height n - 1
    draw(n - 1);

    // Draw one more row of width n
    for (int i = 0; i < n; i++)
    {
        printf("#");
    }
    printf("\n");
}

As we saw with **merge** sort, **recursion** can greatly improve the effeciency of a sorting **algorithm**. 