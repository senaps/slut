# SLUT - Senaps Level Up Track
slut is a project that I will write down what I have learned till now and continue to update it with what I must learn in the future to become a better software engineer.

## Programming Languages
so many thing's about a programming language, including frameworks, howto's and ... this is where I would list them all
### General Q/A
**talk about `Object introspection`**
introspection is the ability to determine the type of an object at runtime

### python
#### General Q/A
these guys are sort of interview question thing going on :)

**what are built-in types in python?**
  - Immutable
    ** string -> str
    ** number -> int, float, complex
    ** sets: tuple, frozenset, bytes
  - Mutable
    ** list, set, dict

**talk about python memory management**
  - python uses reference counting
  - when references to an object get's to 0, garbage collector removes the object from memory automatically.
  - reference increases when `assigned` or when put in a container like `list`, `dictionary` or a `set`.
  - references decrease by `going out of scope`, `del` or being `reassigned`
  
**functions are first class objects, what does it mean?**
  - functions are objects, 
  - can be passed as arguments
  - can be returned from function
  - can be defined inside other functions
  - can be referenced or assigned to a variable

**what is different between list and tuple**
  - list is mutable while tuple immutable
  - list is copied, tuple is reused(since immutable)
  - size is smaller for tuples

**what is `with`?**
  - context manager, encapsulates common cleanup and setup for object
  - replaces `try...finally` ensuring cleanup takes place even if exception happens.

**talk about `range()` and `xrange()`**
  - no more xrange in python3, only range
  - in python2, range would return a range object, while xrange would return a generator object
  - python3 range would return a generator object though.

**`list.append()` vs `list.extend()`**
  - append add's the object as is. while extend will unpack it
  - [1,2,3].append([2,3]) -> [1,2,3,[2,3]]
  - [1,2,3].extend([2,3]) -> [1,2,3,2,3]
  - [1,2,3].extend("string") -> [1,2,3,'s','t','r','i','n','g']
  - [1,2,3].extend({"key": "value"}) -> [1,2,3,'value']
  - [1,2,3].extend((1,2,3)) -> [1,2,3,1,2,3]

**talk about `namespace`?**
  - it's the world inside a scope, we have some scopes like `global`, `local` scope. there is a `built-in` namespace too.
  - namespace is where python would look for variables and functions and etc.

#### a bit deeper than above
**talk about `mangling` or `private class member`**
- identified by `__` or `_`
- replaced with `_calssname__<member>`
- it wont stop access, it's for avoiding accidents
- it help's with debugging too
  
**talk about `mro`?**
- Method Resolution Order
- the order in which Python looks for a method in a hierarchy of classes.
- from Left to Right

**talk about python compiling?**
- translate `.py` to `.pyc(bytecode)` and updating it 
- .pyc being ran by `pvm - python virtual machine`
  
**`cpython` and `python`?**

- cpython is the default python implementation, there are other implementations using java,...
- python is the actual language, cpython convert's the code to byetcode, then runs it.
- `cython` is some other application that translates python to c, but it's not cpython. 
- cpython is developed in C.
- other python implementations in theory should be able to run and get same result from the python code.

**what is `cython` then?**
  - cython is a programming language
  - it is compiled and has a python-c like syntax
  - it is meant to be used to create cpython modules
  - it's supposed to give c like performance 

**Why aren't python nested functions called closures?**

A closure occurs when a function has access to a local variable from an enclosing scope that has finished its execution.

    def make_printer(msg):
        def printer():
            print msg
        return printer

    printer = make_printer('Foo!')
    printer()

When make_printer is called, a new frame is put on the stack with the compiled code for the printer function as a constant and the value of msg as a local. It then creates and returns the function. Because the function printer references the msg variable, it is kept alive after the make_printer function has returned.

So, if your nested functions don't:

    1- access variables that are local to enclosing scopes,
    2- do so when they are executed outside of that scope,

then they are not closures.
Here's an example of a nested function which is not a closure.

    def make_printer(msg):
        def printer(msg=msg):
            print msg
        return printer

    printer = make_printer("Foo!")
    printer()  #Output: Foo!


    
#### Design Q/A
these are sort of an interview/real world design of application sort of thing going on. like how to structure the app and stuff like that:)
**How to import global variable across files?**
write them all in a single file, I use `shortcuts`, `extenstions`, etc... based on what they do in my code, and import them from there
  