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
