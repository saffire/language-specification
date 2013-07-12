###############
Data structures
###############


Data structures are first-class citizens in Saffire. 

Every data structure is handled the same way:

	<structure>[key:val1:val2,key:val1:val2,...]

A list can be defined as:

::

	list["foo", "bar", "baz"];

If a data structure has multiple arguments per element (like a key/value pair), you can separate them with a ``:``

::

	hash["foo":1, "bar":2, "baz":3];

More values are possible too, for instance, a priority-queue, which not only has key/value pairs, but also an additional
priority.

::

	priority["foo":1:10, "bar":2:10, "foo":3:20];


There are 3 internal data structures available:

- `List`_
- `Hash`_
- `Set`_

It's possible to create your own data structures. Be advised that by using custom data structures, you sacrifice
memory and speed compared to the native data structures. Your structure will never be as fast as the native ones.



List
----
Lists are data structures with values only. A value can be available multiple times inside the list 

::

	a = list[ "foo", "bar", "baz" ];

this represents a list of three Strings, which can be accessed through the ``[index]`` notation:

::

	a[0]  // "foo"
	a[1]  // "baz"
	a[2]  // "bar"



Hash
----
Hashes have the same properties as lists, but each value has a unique key.


::

	a = hash[ 1:"foo", 2:"bar", "test":"baz" ];

	a[1]       // "foo"
	a["test"]  // "baz"



Set
---
Sets are like lists, but can only hold unique values. Every time a value is added that already exists, that value will
be ignored.


::

	a = [[ "foo", "bar", "baz", "foo", "bar" ]];
	// a holds "foo", "bar" and "baz"

Sets can be used to quickly add, subtract or check items.



Tuples
------
Tuples work a bit differently than the other data structures. A tuple isn't a data structure like others inside Saffire,
but it's an immutable structure that can hold one or more other elements. Once a tuple has been created, you cannot add
or remove any elements to it.

::

	a = ( "foo", "bar" );

In this example, 'a' would be a tuple with two elements: the string "foo" and the string "bar". A tuple is defined by
using parenthesis and a comma-separated list of items.

::

	a, b, c = "foo", ("bar", "baz"), "qux";

	// a = "foo"
	// b = ("bar", "baz")
	// c = "qux";


Single element tuples
~~~~~~~~~~~~~~~~~~~~~

Defining a tuple with only one element is a bit tricky. This is because syntax-wise this is the same as a grouped
expression. There is no way for saffire to figure out what you want to achieve with the following code:

::

	a = (2 * (3 + 4));


Do you want a to be a tuple, or is it just a expression that you have grouped in order to get the precedence right?
In order to make tuples with a single value, you MUST add a trailing comma at the end of the list. The following would
create a tuple with one element:

::

    a = (2,);    // tuple with the numerical value 2
    b = (2);     // just a numerical value 2

There is no way to create empty tuples, as this is considered pointless.

Using tuples
~~~~~~~~~~~~

Using tuples is fairly easy:

::

    a = (1, 2);     // a is a tuple

But you can also assign something to a tuple:

::

    (a,b) = (1, 2);

Here we assigned the tuple (1,2) to the tuple (a,b). In effect assigning the value 1 to a, and the value 2 to b. It's
even possible to quickly swap variables without a third variable:

::

    (a,b) = (b,a);

When assigning tuples, you don't need to have the same amount of elements. For instance, the following will work:

::

    (a, b) = (1, 2, 3, 4);

In this case, 'a' becomes 1, 'b' becomes 2, but the values 3 and 4 are never assigned. Note however, they will be
evaluated:

::

    (a, b) = (f.foo(), f.bar(), f.baz(), f.qux());

Here, the methods foo(), bar(), baz() and qux() are called, but only the result from foo() and bar() are stored inside
respectively a and b.

The other way around is possible too, you can have more elements on the left-hand side than on the right hand side:

::

    (a,b,c,d) = (1,2);

Here, a becomes 1, b becomes 2, but both c and d are filled with a "null" object. When elements counts do not match up,
Saffire will pad them with "null" to even out the elements.




:Authors:
   Joshua Thijssen
   Caspar Dunant
