1. In LinkedList::deleteFront(), why does it take two separate delete calls instead of one?
   Name exactly what each one frees, and name the two new calls back in the program responsible
   for putting them on the heap in the first place.

The destructor must call delete on both the object and its pointer so we don't end up with a 
nullptr.

2. ArrayList never had a destructor before today. Explain, in your own words, why switching
   from T data[CAPACITY] to T* data[CAPACITY] is what made a destructor necessary, and what
   would happen if you forgot to write one. Would you get a compiler error? Why or why not?

A destructor was not necessary at first because no dynamic memory was being created in the heap.
If we don't use a destructor, there would be no compiler error, but it would instead result in a 
memory leak during runtime as new `ArrayList` objects are created.

3. search() and addFront() both take a T*, but they treat that pointer completely differently.
   Explain the difference in terms of ownership: which one is allowed to delete what you hand it,
   and which one is never allowed to?

`addFront()` is allowed to delete the pointer's reference because it needs to have it point to a 
new value. `search()`, on the other hand, does not need to manipulate data and simply returns 
whether the given value was found.

4. You swapped LinkedList<T> for ArrayList<T> inside makeList() and reran main.cpp without
   changing a single line there. What two mechanisms, by name, made that possible?

Polymorphism of the methods between the two classes allows either call under `makeList()` to work.

5. Pick one keyword from the Key Terms glossary that you either had to add today or wouldn’t have
   thought to add on your own (explicit, override, virtual, const, or any other). Describe, in
   your own words and without copying the guide’s wording, the smallest example you can think
   of where leaving it out would cause a real problem.

The keyword I was least familiar with was `virtual`. This allows us to use same function across 
multiple classes and selected based on the given object type. If we had not used this keyword, 
we would not be able to call `ArrayList` and `LinkedList` interchangeably as we did under 
`makeList()`.