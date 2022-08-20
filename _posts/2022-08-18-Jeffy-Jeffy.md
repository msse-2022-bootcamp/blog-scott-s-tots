---
layout: post
title: "Files, Files, Everywhere!"
author: Jeffy Jeffy
---

Today, we learned about multi-file projects in C++, how they are organized, how to use them, and some "rules" about best practices. So let;s get filin'! 


### Forward Declarations

Say, if we have a multi-file project and one particular file contains some of the functions that maybe useful in our current project. One of the ways of accessing those functions is by forward declaration. This is simply done by declaring the function a.k.a. writing the function signature before the main function of the code. What this truly does is that, it provides the compiler with all the information needed to go look for that function so that during the linking process, it is linked to the main and completes the process. A function can be declared as many times as needed; however, it is not the convention, instead we use the header files to conduct this operation. 

### #include<>

Before we get into what header files are, let's talk about the "include" keyword. One of the first things we learned in C++ was about using "#include <module>" to utilize various functions such as printing to the screen, using a vector, math functions, nad so much more. What #include keyword really does is tells the compiler to copy and paste the content from the said file to the current code. We can see the entire content of the file using -E argument with g++. This prints to the screen a very long (read: very very very long) output that also contains the code for all the include statements that were introduced in the file. 

### Header file 

Header files are essentially a file that contains all the functions for a source file. This may seem like extra work but it really just prevents clutter in source files. The alternative was to manually place declarations in each source file, but this is noisy and can cause errors. Additionally, this also minimizes the exposure of information to users. It is also a great place to list documentation for all the functions. The way to call a source file is through the include statement mentioned above. By using #include<headerfilename>, the compiler will find the header file, find the function signature and the definitions for those signatures, and copy and paste them in the file where it was called. During, the linking process, these functions are then used as they are called. Compilers and linkers are working very hard and are very smart! 

Before we go any further, it is important to also recognize that sometimes a header file can get included twice from a single source file -- specially if it is a large project. To prevent this from happening, we can include #pragma once at the top of the header file so it does not get included twice. 

Before we end, important notes about using the header file:  
    1. Never #include a .cpp file 
    2. Only #include a header file 
    3. Source file can include header file and header file can include a header file but we never include the source file. 
    4. We never compile the header files because they get included in the source files. 
    5. Pay attention to the naming conventions. 
    6. Include your libraries in your source file and your header file.

Happy filing! 
