# Basics of C programming
1. linked list examples:https://www.thegeekstuff.com/2012/08/c-linked-list-example/
2. working with time and dates：https://www.codingunit.com/c-tutorial-how-to-use-time-and-date-in-c
3. pseudo-random numbers:http://www.tutorialspoint.com/c_standard_library/c_function_rand.htm
4. string functions:https://en.wikibooks.org/wiki/A_Little_C_Primer/C_String_Function_Library

# Command lines
- Read man pages (man)
- Navigate directories (cd, ls, pwd)
- Move and copy files (mv, cp)
- Adjust permissions or groups (chown, chmod)
- Run executables (gcc, C executables, or other tools)

# A simple command line hello world
```bash
# navigate to home dir
$ cd ~

# create main.c file
$ touch main.c

# edit main.c (write program)
$ nano main.c

# compile (and link) program
$ gcc main.c -o helloWorld

# run program
$ ./helloWorld

```
# Make files
Using Makefiles
When building large, maintainable C programs (with multiple entry points and shared code), the use of Makefiles is paramount. In this course, students must submit their projects using Makefiles to automate the build process of their C program(s). This will allow our graders to more quickly grade student submissions and provide timely feedback.

- https://www.gnu.org/software/make/manual/make.html
- http://mrbook.org/blog/tutorials/make/

```bash
# specify the compiler
CC=gcc

# specify options for the compiler
CFLAGS=-c -Wall

all: hello

hello: main.o hello.o
    $(CC) main.o hello.o -o hello

main.o: main.cpp
    $(CC) $(CFLAGS) main.cpp

hello.o: hello.cpp
    $(CC) $(CFLAGS) hello.cpp

clean:
    rm -rf *o hello

```
# HOME PAGE
https://www.cc.gatech.edu/~ada/
