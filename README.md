<<<<<<< HEAD

# _printf
```_printf``` is a custom implementation of the C programming function ```printf```.
**Prototype:** ```int _printf(const char *, ...);```

## Some Examples

**Integer**

* Input: ```_printf("There are %i dozens in a gross\n", 12);```
* Output: ```There are 12 dozens in a gross```

**Character**

* Input: ```_printf("The first letter in the alphabet is %c\n", 'A');```
* Output: ```The first letter in the alphabet is A```

**String**

* Input: ```_printf("%s\n", 'This is a string.');```
* Output: ```This is a string.```

**Decimal:**

* Input: ```_printf("%d\n", 1000);```
* Output:  ```1000```

**Rot13**

* Input: ```_printf("Unknown:[%R]\n", "HELLO WORLD");```
* Output:  ```URYYB JBEYQ```

**FLAGS**

* Input: ```printf("Flag: [%+ d]", 1230);```
* Output:  ```Flag: [+1230] => 13```

**OCTAL**

* Input: ```printf("Unsigned octal:[%o]", 6);```
* Output:  ```Unsigned octal:[6] => 18```

## Project Requirements

* All files will be compiled on Ubuntu 14.04 LTS
* Programs and functions will be compiled with gcc 4.8.4 using flags -Wall -Werror -Wextra and -pedantic
* Code must follow the [Betty] style
* Global variables are not allowed
* Authorized functions and macros:

  * ```write``` (man 2 write)
  * ```malloc``` (man 3 malloc)
  * ```free``` (man 3 free)
  * ```va_start``` (man 3 va_start)
  * ```va_end``` (man 3 va_end)
  * ```va_copy``` (man 3 va_copy)
  * ```va_arg``` (man 3 va_arg)

## Mandatory Tasks

- [x] Write function that produces output with conversion specifiers ```c```, ```s```, and ```%```.
- [x] Handle conversion specifiers ```d```, ```i```.
- [x] Create a man page for your function.

## Advanced Tasks

- [x] Handle conversion specifier ```b```.
- [x] Handle conversion specifiers ```u```, ```o```, ```x```, ```X```.
- [x] Use a local buffer of 1024 chars in order to call write as little as possible.
- [x] Handle conversion specifier ```S```.
- [x] Handle conversion specifier ```p```.
- [x] Handle flag characters ```+```, space, and ```#``` for non-custom conversion specifiers.
- [ ] Handle length modifiers ```l``` and ```h``` for non-custom conversion specifiers.
- [ ] Handle the field width for non-custom conversion specifiers.
- [ ] Handle the precision for non-custom conversion specifiers.
- [ ] Handle the ```0``` flag character for non-custom conversion specifiers.
- [x] Handle the custom conversion specifier ```r``` that prints the reversed string.
- [x] Handle the custom conversion specifier ```R``` that prints the rot13'ed string.
- [ ] All above options should work well together.

## File Descriptions

**_printf.c**

* contains the  fucntion ```_printf```, which uses the prototype ```int _printf(const char *format, ...);```. The format string is composed of zero or more directives. See ```man 3 printf``` for more detail. **_printf** will return the number of characters printed (excluding the null byte used to end output to strings) and will write output to **stdout**, the standard output stream.

**_putchar.c**

* contains the function ```_putchar```, which writes a character to stdout.

**main.h**

*contains all function prototypes used for ```_printf```.

**man_3_printf**

* manual page for the custom ```_printf``` function.

**functions.c** **functions1.c** **functions2.c**

* contains all function of each specifier used for ```_printf```.

* all function have its own description inside the file.

**handle_print.c**

* contains arguments types used for ```_printf```.

**get_flags.c**

* contains all function for each flag use for ```_printf```.

**utils.c**

* contains some necessary functionalities for ```_printf```.

**ger_width.c**

* contains functions to get width for spcifics spcifiers.

**writee_handlers.c**

* contains write functions.

By Leo Azubuike and Olusegun Alawode

=======

Compilation

Your code will be compiled this way:
$ gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c

As a consequence, be careful not to push any c file containing a main function in the root directory of your project (you could have a test folder containing all your tests files including main functions)

Our main files will include your main header file (main.h): #include main.h

You might want to look at the gcc flag -Wno-format when testing with your _printf and the standard printf. Example of test file that you could use:

alex@ubuntu:~/c/printf$ cat main.c

#include <limits.h>
#include <stdio.h>

#include "main.h"

/**
 * main - Entry point
 *
 * Return: Always 0
 */

int main(void)
{
    int len;
    int len2;
    unsigned int ui;
    void *addr;

    len = _printf("Let's try to printf a simple sentence.\n");
    len2 = printf("Let's try to printf a simple sentence.\n");

    ui = (unsigned int)INT_MAX + 1024;
    addr = (void *)0x7ffe637541f0;

    _printf("Length:[%d, %i]\n", len, len);
    printf("Length:[%d, %i]\n", len2, len2);
    _printf("Negative:[%d]\n", -762534);
    printf("Negative:[%d]\n", -762534);
    _printf("Unsigned:[%u]\n", ui);
    printf("Unsigned:[%u]\n", ui);
    _printf("Unsigned octal:[%o]\n", ui);
    printf("Unsigned octal:[%o]\n", ui);
    _printf("Unsigned hexadecimal:[%x, %X]\n", ui, ui);
    printf("Unsigned hexadecimal:[%x, %X]\n", ui, ui);
    _printf("Character:[%c]\n", 'H');
    printf("Character:[%c]\n", 'H');
    _printf("String:[%s]\n", "I am a string !");
    printf("String:[%s]\n", "I am a string !");
    _printf("Address:[%p]\n", addr);
    printf("Address:[%p]\n", addr);
    len = _printf("Percent:[%%]\n");
    len2 = printf("Percent:[%%]\n");
    _printf("Len:[%d]\n", len);
    printf("Len:[%d]\n", len2);
    _printf("Unknown:[%r]\n");
    printf("Unknown:[%r]\n");

    return (0);
}

We strongly encourage you to work all together on a set of tests
If the task does not specify what to do with an edge case, do the same as printf

Tasks

### [0. I'm not going anywhere. You can print that wherever you want to. I'm here and I'm a Spur for life]

* Write a function that produces output according to format.

  - c : converts input into a character
  - s : converts input into a string

### [1. Education is when you read the fine print. Experience is what you get if you don't]

* Handle the following conversion specifiers:

  - d : converts input into a base 10 integer
  - i : converts input into an integer

### [2. Just because it's in print doesn't mean it's the gospel]

* Create a man page for your function

### [3. With a face like mine, I do better in print]

* Handle the following conversion specifiers:

  - b : the unsigned int argument is converted to binary

### [4. What one has not experienced, one will never understand in print]

* Handle the following conversion specifiers:

  - u : converts the input into an unsigned integer
  - o : converts the input into an octal number
  - x : converts the input into a hexadecimal number
  - X : converts the input into a hexadecimal number with capital letters

### [5. Nothing in fine print is ever good news]

* Use a local buffer of 1024 chars in order to call write as little as possible.

### [6. My weakness is wearing too much leopard print]

* Handle the following custom conversion specifier:

  - S : prints the string
  - Non printable characters (0 < ASCII value < 32 or >= 127) are printed this way: \x, followed by the ASCII code value in hexadecimal (upper case - always 2 characters)

### [7. How is the world ruled and led to war? Diplomats lie to journalists and believe these lies when they see them in print]

* Handle the following conversion specifier:

  - p : int input is converted to a pointer address

### [8. The big print gives and the small print takes away]

* Handle the following flag characters for non-custom conversion specifiers:

  - \+ : adds a \+ in front of signed positive numbers and a \- in front of signed negative numbers
  - space : same as \+, but adds a space (is overwritten by \+)
  - \# : adds a 0 in front of octal conversions that don't begin with one, and a 0x or 0X for x or X conversions

### [9. Sarcasm is lost in print]

* Handle the following length modifiers for non-custom conversion specifiers:

  - l : converts d, i, u, o, x, X conversions in short signed or unsigned ints
  - h : converts d, i, u, o, x, X conversions in long signed or unsigned ints

### [10. Print some money and give it to us for the rain forests]

* Handle the field width for non-custom conversion specifiers.

### [11. The negative is the equivalent of the composer's score, and the print the performance]

* Handle the precision for non-custom conversion specifiers.

### [12. It's depressing when you're still around and your albums are out of print]

* Handle the 0 flag character for non-custom conversion specifiers.

### [13. Every time that I wanted to give up, if I saw an interesting textile, print what ever, suddenly I would see a collection]

* Handle the - flag character for non-custom conversion specifiers.

### [14. Print is the sharpest and the strongest weapon of our party]

* Handle the following custom conversion specifier:

  - r : prints the reversed string

### [15. The flood of print has turned reading into a process of gulping rather than savoring]

* Handle the following custom conversion specifier:

  - R : prints the rot13'ed string

### [16. * ]

* All the above options work well together.

---

### Authors

* **Maduabughichi Achilefu** - [aachilefu@yahoo.com](https://github.com/maduoma)

* **
Repo:

GitHub repository: printf