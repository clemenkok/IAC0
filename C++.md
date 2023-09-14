# C++ and OOP

Prior to the commencement of second year, familiarising yourself with C++ features not covered in Year 1 programming such as smart pointers, maps and lambda functions allows for faster progress in the Instruction Architectures and Compilers module, as well as providing a solid base for software development in industry.

A lot of the content in this section will be more easily understood if you read the Key Notes at the end, especially for RAII, as they were written hand-in-hand.

## Contents
- [C++ and OOP](#c-and-oop)
  - [Contents](#contents)
  - [Smart Pointers](#smart-pointers)
    - [std::unique\_ptr](#stdunique_ptr)
    - [std::shared\_ptr](#stdshared_ptr)
    - [std::weak\_ptr](#stdweak_ptr)
  - [Lambda Functions](#lambda-functions)
  - [RAII](#raii)
  - [Key Notes on C++ and Compilers:](#key-notes-on-c-and-compilers)
  

## Smart Pointers

There are four types of smart pointer in modern C++:

- std::auto_ptr;
- std::unique_ptr;
- std::shared_ptr;
- std::weak_ptr;

### std::unique_ptr

Generally, **std::unique_ptr** accomplishes everything that **std::auto_ptr** is capable of, whilst **std::auto_ptr** is only used if you need to compile C++98 code. **std::unique_ptr** is the most commonly used smart pointer, and is for **exclusive-ownership resource management.** They work the same as raw pointers, and for most operations, including **dereferencing,** they execute the same instructions.

**Exclusive-ownership resource management** in the context of unique::ptrs means to own the object they point to, and moving such a pointer involves transferring ownership from the source pointer to the destination, whilst setting the source pointer to **NULL.**

These pointers cannot be copied, as that would result in multiple pointers thinking they owned the same resource, destroying it. Upon destruction, a **non-NULL std::unique_ptr** destroys its' resource.

### std::shared_ptr

**std::shared_ptr** is used for **shared-ownership resource management.** When an object has multiple shared pointers, they **collaborate** to ensure its' destruction when it is no longer required. When the final pointer stops pointing there, the object is destroyed.

**Shared pointers** tell whether they are the final pointer to the resource using the resources' **reference count;** this increments and decrements due to shared pointer constructors and destructors respectively.

**NOTE:** Copy constructors do both.

For example, `sp1 = sp2` assuming they are shared pointers to different objects, would reassign sp1 to point to the same object as sp2, decreasing and increasing the reference count of each object respectively.

**std::shared_ptrs** are twice the size of a raw pointer, as they internally contain a raw pointer to the **reference count of the resource.**

Memory for said reference count must be **dynamically allocated,** the reference count cannot be stored on the stack, as it must be shared between all shared pointers to the same resource.

Moving a shared pointer is possible, which transfers ownership of the resource from the source to the destination, whilst setting the source to **NULL.** 

Just like unique pointers, shared pointers use the delete keyword to destroy the resource they point to, but they also support **custom deleters**; however unlike unique pointers, their deleters do not need to be the same type as the pointer.

```
auto loggingDel = [](Widget *pw){   // custom deleter
    makeLogEntry(pw);
    delete pw;
};

std::unique_ptr<Widget, decltype(loggingDel)> upw(new Widget, loggingDel); // deleter type is part of ptr type

std::shared_ptr<Widget> spw(new Widget, loggingDel); // deleter type is not part of ptr type
```

Therefore, the shared pointer type is **more flexible,** as even with custom deleters of different types, they can be put in a container of the pointer's type and passed into functions taking a parameter of type shared_ptr<Widget>.

Custom deleters can be function objects, containing arbritrary amounts of data - a pointer can't refer to such a deleter without using more memory, but it can use more memory from the heap or as per the shared pointer's custom allocator.

std::make_shared **always** creates a control block on the heap; a control block is a larger data structur containing the reference count. There are a set of rules for control block creation, including:

- std::make_shared always creates a control block, and manufactures a new object to point to.
- A control block is created when a shared pointer is constructed from a unique pointer.
- The shared pointer assume ownership of the pointed to object, and the unique pointer is set to NULL.

Shared pointer constructors taking shared or weak pointers as constructor arguments **do not** create a control block, but instead **share** the control block of the argument.

These rules result in the consequence of not being able to construct more than one shared pointer from a single raw pointer, else it can lead to undefined behaviour.

Key notes on shared pointers:

- They are twice the size of a raw pointers, incur overhead for control blocks and require atomic reference count manipulations.
- They offer convenience approaching that of garbage collection for the shared lifetime management of arbritrary objects.
- Default resource deletion is via delete, but custom deleters are supported.
- Avoid created shared pointers from raw pointers.

### std::weak_ptr

Use weak pointers for pointers similar to shared pointers, which can dangle. They don't affect the reference count of the resource they point to, and they don't own the resource they point to. They are not standalone pointers, and can only be created from shared pointers. Weak pointers that dangle are said to have **expired**.


## Lambda Functions

A lambda function is an **anonymous function** that can be used to replace a function pointer. They are useful for **one-off functions** that are only used once, and are not required to be named.

NOTE: still to complete

## R-values and L-values

R-values can be thought of as temporary objects that can't be assigned a value, whereas l-values can be thought of as an object to which you *can* assign a value. 

Expressions that refer to memory locations are "l-values" and if those locations are modifiable, they are "modifiable l-values". L-values represents a storage region's "locator" value or a "left" value, implying that it can appear on the left of the equal sign. 

The term "r-value" is sometimes used to descrive the value of an expression and to distinguish it from an l-value, however you need to keep in mind **all l-values are r-values, but not all r-values are l-values.**

## RAII

In depth video on RAII: https://www.youtube.com/watch?v=7Qgd9B1KuMQ - from which a lot of the notes are taken

**Resource Acquistiom is Initialization, is a C++ programming technique that binds the life cycle of a resource that must be acquired before use to the lifetime of an object.** Some resources this applies to includes allocated heap memory, thread of execution, open socket, open file, locked mutex, disk space or database collection - anything that exists in limited supply.

More generally, it is the principle that there is some *explicit* action that we need to take in the program in order to *free* the resource - think how you deleted all the pointers in Assignments 2 & 3 in Year 1, using `delete[]`.

Hence, if you class directly manages some kind of resource (like a raw pointer), then you should hand-write these three special member functions:
- A **destructor** to free the resource
- A **copy constructor** to copy the resource
- A **copy assignment operator** to free the left-hand resource and copy the right-hand one

Use the copy-and-swap idiom to implement assignment; this is done to prevent issues when self-copying e.g. `v = v`. We make a **complete** local copy of the right-hand side, *prior* to the first modification to `this` object. This matters even more when writing templated or recursive data structures.

Destructors help us write code that is robust against exceptions, as they make the runtime look "up the call stack" until it finds a suitable `catch` handler for the type of exception being thrown. If it finds one, the runtime performs **stack unwinding** where for every local scope between the throw and catch handler, the runtime calls the destructors of all local variables in the scope.

To avoid leaks, place all **cleanup** code in **destructors.**

Below, you can see that here the code calls `new` but fails to call `delete` when an exception is thrown, as stack unwinding, which is aforementioned, skips us down to the `catch` meaning we don't execute the skipped over line. This means this is not good RAII code, as it leaks memory.

```
int main(){
    try {
        int *arr = new int[4];
        throw std::runtime_error("for example");
        delete [] arr; // cleanup
    } catch (const std::exception& ex) {
        std::cout << "Caught an exception: << ex.what() << "\n";  
    }
}
```

To rectify this issue, we can write a simple `struct`, that contains our pointer to an int, and a constructor & destructor, that deletes our pointer. By putting the responsibility for cleanup into our destructor, which is called when the array goes out of scope during stack unwinding, exceptions will not cause memory leaks. See the amended code below.

```
struct RAIIPtr {
    int *ptr_;
    RAIIPtr(int *p) : ptr_(p) {} // constructor
    ~RAIIPtr() {delete [] ptr_;} // destructor
};

int main(){
    try {
        int *arr = new int[4];
        throw std::runtime_error("for example");
    } catch (const std::exception& ex) { // cleanup is called at the first curly brace
        std::cout << "Caught an exception: << ex.what() << "\n";  
    }
}
```

This is still relatively dangerous code, as `RAIIPtr` still has a defaulted copy constructor and a copy assignment operator.

to be continued...

## Key Notes on C++ and Compilers:

- Initialization is not the same as assignment, assignment is using an already existing object, initialization is creating a new one. Initialization of a new object calls a copy constructor, assignment to existing objects calls the assignment operator.
- Destructors are used in C++ to free resources and avoid *leaks*, copy constructors are responsible for duplicating resources to avoid *double frees*.
- When writing a destructor, you need to write a *copy constructor and a copy assignment operator.*
- 
- 
- 
- 
- A good resource to learn what safety in C++ is: https://www.youtube.com/watch?v=CWglkNBUmD4

