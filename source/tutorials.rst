#########
Tutorials
#########

Hello world
-----------

::

    import io;

    io.print("hello world!");

In order to use methods like print, you must include the actual module that defines this functionality. The ``io`` class
defines input and output functionality, including methods like ``print`` and ``printf``.


Simple calculations
-------------------

::

    import io;

    a = 1;
    a += 1;

    io.print("The value of a: ", a , "\n");

Variables do not have to be declared, but can be directly instantiated. Using uninstantiated variables will result in
an exception. Variables inside strings aren't automatically converted to their values. Using ``a`` inside a string will
result in a **literal** ``a``. If you want to use the **value** of ``a``, you must add them separately. The print method
allows multiple arguments so you can easily concatenate the string and values.


Classes and Objects
-------------------

::

    import io;

    class foo() {
        protected property a;

        public method __ctor(a) {
            self.a = 1;
        }

        public method bar() {
            return self.a;
        }
    }

    f = foo();
    io.print (f.bar());

    // You can even instantiate and the instance directly.
    io.print (foo().bar());


Data structures & iterators
---------------------------

::

    import io;

    // Define a list
    mylist = list[[1, 2, 3, 4, 5]];


    // Part = list[1,2,3]
    part = mylist[0..2];

    // Part = list[3,4]
    otherpart = mylist[2..3];


    foreach (list as v)  {
        io.print(v, "\n");
    }
    // returns 1 2 3 4 and 5



    // Even a string is a datastructure that can be iterated
    foreach ("mystring" as v) {
        // v is a string with one character
        io.print(v, "\n");
    }

Creating and using data structures is Saffire is easy. A class is considered a datastructure when it implementes the
``datastructure`` interface. This interface allows you to define your datastructures like:

::

    mydatastructure[[ key:value, key2:value2 ]];

In order to iterate a datastructure, your object must also implement the ``iterable`` interface so they can be used
in ``foreach`` loops. Saffire has a few core objects that are both implement ``datastructure`` and ``iterable``, for
instance: ``hash``, ``list``, ``tuple`` and ``string``.


:Authors:
   Joshua Thijssen
   Caspar Dunant
