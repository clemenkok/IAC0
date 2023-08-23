# C++ and OOP

Prior to the commencement of second year, familiarising yourself with C++ features not covered in Year 1 programming such as smart pointers, maps and lambda functions allows for faster progress in the Instruction Architectures and Compilers module, as well as providing a solid base for software development in industry.

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
