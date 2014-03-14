############
Scalar types
############

Saffire is an object-only language. This means that everything, including strings, numerical values etc, are objects.

**String**
    This represents an binary safe string of characters. The ``length()`` of a string will always return the number of
    CHARACTERS, which is not always the actual number of bytes, depending on which encoding you have used. Make sure
    that when dealing with binary data, you are using ``String.bytes()`` instead of ``String`` in order to retrieve the
    actual bytes.

**Numerical**
    Numeric integer ranging from ``Numerical.MIN`` to ``Numerical.MAX``. Longer numerical values can use a different class
    (LongNumeric) instead.

**Double**
    Any fixed point number. Note that Saffire does not have floating point numbers.

**Boolean**
    Representing either a true or a false value.

**Exception**
    The base exception class. Has a ``getMessage()`` and ``getCode()`` method.

**Hash**
    A hash datastructure holds key->value pairs.

**List**
    A list datastructure holds only values.

**Tuple**
    A datastructure that holds a certain number of elements. Can be used with the () shortcut.

::

    // Both lines does the same thing
    mytuple = (1,2);
    mytuple = tuple[[1,2]];

    // pad tuples with null values
    (a,b,c) = (1,2);
    // c = NULL

    // Easily switch variables by packing and unpacking tuples
    (a,b) = (b,a)

**Regex**
    A regular expression class.

**Null**
    A null class represents a null value.


Instances
---------
There are a few pre-instantiated objects.

**Null**
    Represents a null value.

**True**
    A boolean representing a true value.

**False**
    A boolean representing a false value.


Casting to objects
------------------

Casting strings
===============

* string.numerical()
    Converts the numerical value into a string by the following rules:

    * strips away any white-spaces in front of the string.
    * A '-' in front of the string will negate the actual value (eg: -5)
    * when '0x' is encountered, the string will be treated as a hexidecimal string.
    * when a '0' is encountered, the string will be treated as a octal string.
    * when a 'b' is encountered, the stirng will be treated as a binary string.
    * the method will parse as many valid characters as possible and stops after finding the first
      invalid character (or when the string ends).

    =====================  =====  ==============
    Code                   Value  Extra info
    =====================  =====  ==============
    "123".numerical()        123
    "-5".numerical()          -5
    "123ab".numerical()      123
    "0x1AG".numerical()       26  (hex: 0x1a)
    "0x123ab".numerical()  74667  (hex: 0x123ab)
    "b11".numerical()          3  (binary: 11)
    "b112".numerical()         3  (binary: 11)

    "010".numerical()          8  (octal: 10)
    "10".numerical()          10
    "018".numerical()          1  (octal: 1)
    =====================  =====  ==============


* string.boolean()
    If the string value is empty (""), it will return a boolean FALSE, otherwise it will return a boolean TRUE.

* string.null()
    Returns a NULL object.


Casting numericals
==================

* numerical.string()
    Returns a string representation of the numerical value.

* numerical.boolean()
    If the value is 0, it will return boolean FALSE, otherwise it will return a boolean TRUE.

* numerical.null()
    Returns a NULL object.


Casting booleans
================

* boolean.string()
    Returns the string "true" when the value is TRUE, returns the string "false" when the value is FALSE.

* boolean.numerical()
    Returns numerical 0 when the value is FALSE, returns numerical 1 when the value is TRUE;

* boolean.null()
    Returns a NULL object.


Casting null
============

* null.string()
    Returns the string value "null".

* null.numerical()
    Returns a numerical value 0.

* null.boolean()
    Returns a boolean FALSE.



:Authors:
   Joshua Thijssen
