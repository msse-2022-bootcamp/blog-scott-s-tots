---
layout: post
title: "Pointers, References, and more"  
author: Yangyi Hao 
--- 

###### Types and Sizeof

We started off by discussing that each different variable may come at different sizes, for example an int would come at 4 bytes, and a double would come at 8 bytes, and its reason is that they have different types. Some types that are more descriptive naturally need more bytes to describe all the information needed.

Primitive types can be initialized to a default value if not set. Usually that would be their types' way of intepretating "0". For example to a boolean, that would become a "false".

Non-primitive types do not come with default initializers unless explicitly created. They are usually just a pointer that points to an address, and forcefully interpreting zeros out of those addresses would just result in garbages.

###### Arrays, Pointers and References

We then moved on to discuss arrays, pointers, and references, which may be arguablly the most interesting topics in C++.

There are c-style arrays, which are essentially pointers that point to addresses, or vectors, which are "containers". We can perform pointer arithmetics on c-style arrays and usually, they come with stricter rules on sizes and emptiness as well. Maybe just use vectors :)

We do have to deallocate arrays if they were dynamically allocated. Dynamical allocation is when the size of an array is not known at compile time. Having to "delete" a variable seems like a very messy process. We can either use the "constexpr" keyword on the size variable so that it's known at compile time, or we can use vectors, or we can also swicth to Java, which comes with garbage collections :)

Lastly, we moved on to the topics of references. References can be easily confused with pointers, they seem so similar and they are. An easy way to understand their difference though, is to think that a reference is just really a different name of the same thing. At compile time, references will be interpreted to the same addresses as the thing they were referencing to, so they are really just the same thing. Yet a pointer, that points to something, is actually a complete different thing by itself.
