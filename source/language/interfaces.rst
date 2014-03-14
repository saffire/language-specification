##########
Interfaces
##########

Saffire interfaces are a "contract" of methods that a class can implement. They are similar to abstract classes,
however:

* A class can implement multiple interfaces, but only extend one (abstract) class
* An interface can only describe methods, not implement method bodies.
* An abstract class can have abstract methods, but also methods with bodies.

An interface however:

* Can implement other interfaces
* Can have methods, properties and/or constants.


Example:
::

	interface Foo {
		public method Bar(String a);
		public method Baz(String b);
	}

	class Bar implements Foo {
		public method Bar(String a) {
			// Body of method
		}

		public method Baz(String b) {
			// Body of method
		}
	}


Core interfaces
---------------

There are a few core interfaces:

Iterator
~~~~~~~~

*   __iterator()

    Returns an iterator. Will be called by foreach() so your class could actually fetch an external iterator if needed
    (like PHP's iteratorAggregate interface). When your object is by itself an iterator as well, this method would return self.

*   __key()

    Returns the key of the current element.

*   __value()

    Returns the value of the current element.

*   __rewind()

    Rewinds the iterator back to the beginning.

*   __hasNext()

    Returns true when there is another value on the iterator list.

*   __next()

    Moves the iterator to the next element


Datastructure
~~~~~~~~~~~~~

*   __populate()

    Will populate the current datastructure with values (fetched as a list of tuples of items)


Subscription
~~~~~~~~~~~~~

*   __length()

*   __add()

    Add a new value to the object through [].

    ::

        a = list[[]];
        a[] = 1;


*   __remove()

    Removes an element from the object.

*   __get()

    Returns a single value through []

    ::

        a = list[[1,2,3,4]];
        b = a[3];

*   __has()

    returns true if the object has the given index key

*   __splice()

    Returns a part of the object.

    ::

        mylist = list[[1,2,3,4]]
        partial = mylist[1..2];     // 2,3



:Authors:
   Joshua Thijssen
   Caspar Dunant
