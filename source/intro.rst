############
Introduction
############

Welcome to Saffire!

A web-language in the making that tries to bring the best of the current web languages available: Python, PHP and Ruby,
mixed with its own twist.


------------

**Everything is an object**
	Everything in Saffire is an object. This include scalar values like strings, numericals, data-structures, booleans
	and even null.

**No global functions**
	There will be no global functions available. All functionality is focused in classes, for instance, the print()
	method is based in the io class, while all string transformation and manipulation functionality (for instance:
	uppercasing, splicing, searching) are located inside the String object.

**Unicode out of the box**
	All strings are binary safe. A length on a string will return the actual number of characters, not the number of
	bytes. Also all string functions take unicode and collation into account during sorting and conversions.

**Operator overloading**
	It's possible to overload most operators. For instance, it's possible to overload the + operator, so they make sense
	in the context of your own objects.

**Method overloading**
	Depending on the arguments passed, different methods with the same name can be called. Instead of having one single
	method handling all different kind of objects, you can separate them nicely into different methods.

------------

:Authors:
   Joshua Thijssen
   Caspar Dunant
