Alex's Anthology of Algorithms: Common Code for Contests in Concise C++ (A<sup>3</sup>C<sup>5</sup>)
==================

*Note*: You may find the currently available algorithms in a single PDF here: http://alexli.ca/A3C5.pdf. The version you are reading is currently undergoing review
You may also find an **outdated** PDF version here: http://alexli.ca/A3C5-old.pdf.
The PDF version contains only a fraction of algorithms found in this GitHub repository, and a whole multitude of mistakes that are fixed here. Use at your own risk!

## Introduction

This anthology started as a personal project to implement common algorithms in the most concise and "vanilla" way possible so that they’re easily adaptable for use in algorithm competitions. To that end, several properties of the algorithm implementations should be satisfied, not limited to the following:

* Implementations must be clear. There is no time to write rigorous documentation within contests. This makes it all the more important to make class and variable names reflexive of what they represent. Clarity must also be carefully balanced with not making them too long-winded, since it can be just as time-consuming to type out long identifiers.

* Implementations must be generic. The more code that must be changed during the contest, the more room there is for mistakes. Thus, it should be easy to apply implementations to different purposes. C++ templates are often used to accomplish this at the slight cost of readability.

* Implementations must be portable. Different contest environments use different versions of C++ (though almost all of them use GCC), so in order to make programs as compatible as possible, non-standard features should be avoided. This is also why no features from C++0x or above are used, since many constest systems remain stuck on older versions of the language. Refer to the "Portability" section below for more information.

* Implementations must be efficient. The code cannot simply demonstrate an idea, it should also have the correct running time and a reasonably low constant overhead. This is sometimes challenging if concision is to be preserved. However, contest problem setters will often be understanding and set time limits liberally. If an implementation from here does not pass in time, chances are you are choosing the wrong algorithm.

* Implementations must be concise. During timed contests, code chunks are often moved around the file. To minimize the amount of scrolling, code design and formatting conventions should ensure as much code fits on the screen as possible (while not excessively sacrificing readability). It’s a given that each algorithm should be placed within singleton files. Nearly all contest environments
demand submissions to be contained within a single file.

A good trade-off between clarity, genericness, portability, efficiency, and concision is what comprises the
ultimate goal of adaptability.

## Portability

All programs are tested with version 4.7.3 of the GNU Compiler Collection (GCC) compiled for a 32-bit target system.

That means the following assumptions are made:
* bool and char are 8 bits
* int and float are 32 bits
* double and long long are 64 bits
* long double is 96 bits

Programs are highly portable (ISO C++ 1998 compliant), __except__ in the following regards:
* Usage of long long and related features \[-Wlong-long\] (such as LLONG_MIN in \<climits\>), which are compliant in C99/C++0x or later. 64-bit integers are a must for many programming contest problems, so it is necessary to include these.
* Usage of variable sized arrays \[-Wvla\] (an easy fix using vectors, but I chose to keep it because it is simpler and because dynamic memory is generally good to avoid in contests)
* Usage of GCC's built-in functions like __builtin_popcount() and __builtin_clz(). These can be extremely convenient, and are easily implemented if they're not available. See here for a reference: https://gcc.gnu.org/onlinedocs/gcc/Other-Builtins.html
* Usage of compound-literals, e.g. vec.push_back((mystruct){a, b, c}). This is used in the anthology because it makes code much more concise by not having to define a constructor. It is also trivial to fix, so what the heck.
* Ad-hoc cases where bitwise hacks are intentionally used, such as functions for getting the signbit with type-puned pointers. If you are looking for these features, chances are you don't care about portability anyway.

## Usage Notes

The primary purpose of this project is not to better your understanding of algorithms. To take advantage of this anthology, you must have prior understanding of the algorithms in question. In each source code file, you will find brief descriptions and simple examples to clarify how the functions and classes should be used (not so much how they work). This is why if you actually want to learn algorithms, you are better off researching the idea and trying to implement it independently. Directly using the code found here should be considered a last resort during the pressures of an actual contest.

All information from the comments (descriptions, complexities, etc.) come from Wikipedia and other online sources. Some programs here are direct implementations of pseudocode found online, while others are adaptated and translated from informatics books and journals. If references for a program are not listed in its comments, you may assume that I have written them from scratch. You are free to use, modify, and distribute these programs in accordance to the license, but please first examine any corresponding references of each program for more details on usage and authorship. Cheers and hope you enjoy!

Cheers and hope you enjoy!

— Alex Li

