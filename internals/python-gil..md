# Python GIL Details
- Python is single threaded but is capable of multi threading (supports creation and management of multiple threads)
- Meaning it can run multiple tasks (CPU intensive + IO intensive) simultaneously using threads, but it cannot use threads to do different CPU intensive things at the same time due to GIL (Global Interpreter lock)

## Problem - Solutions
### Problem
- Python uses *reference counting* for memory management, that is it maintains a count of number of references to a object. When it reaches zero, the memory occupied by that object is released
- **Issues with reference counting**: python has to keep a count for all objects (using memory to clean memory). Also, there will be an issue if a variable is self referenced
- **Problem**: In case we want to use multiple threads, these reference count variables will need protection from race conditions (can cause leaked memory when memory is never released or the memory can be released early in which case there can be unexpected creashes)
### Solutions
- We can add a lock to each counter (which are shared across threads).
    - But adding many locks means another problem - Deadlocks 
    - Another problem can be decreased performance due repeated aquisition and release of locks
#### Final Solution
- GIL, a single lock on the interpreter
    - controls the execution of any python bytecode (thread should aquire lock and then do anything)
    - a single lock means no performance overhead
    - but makes any CPU-bound Python program single threaded
#### Extra Points
- GIL is also used by interpreter of other languages (like Ruby)
- Other approach than GIL can be introduction of [Garbage Collection](garbage-collection.md)
    - this also means that languages that use Garbage Collector have to add performance booksting features(like JIT compilers) to componsate the loss of single threaded performance benefits
- This limitation of single threaded execution is limited to Cpyhon only, also if the there are lots of IO intensive tasks (thread waiting for Io response), it comparatively has less impact than is expected

## Increasing performance in other ways
- Multiprocessing
- Asynchronous Programming
- C extension
    - can write a C extension to relase the GIL while it runs (done by Numpy and pandas)
- Python implementations other that CPython
    - like Jython, IronPython, PyPy
- Using other Libraries
    - like Numpy, pandas, scipy that handle GIl internally