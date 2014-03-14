############################
Saffire from other languages
############################

Saffire for PHP programmers
---------------------------
There are many differences between PHP and Saffire, even though the language are pretty similar in setup.

- There are no (global) functions.
- Defining methods is done through the ``method`` keyword, instead of ``function``.
- Scalar values like strings and integers are objects too.
- Saffire is strong typed. Saffire will not convert variables from numericals to strings or vice versa without you
  explicitly casting this.
- Saffire strings are always in unicode. The returned length of a string is the number of characters, not the actual
  number of bytes.
- __constructor and __destructor methods are called __ctor() and __dtor() respectively.
- Array's are hashmaps, used as the ``hash[]`` data structure. Numerical arrays are used as ``list[]`` structures.
- Saffire supports method and operator overloading.
- Methods and properties visibilities must be explicitly stated (they are not implied public).
- Saffire support multiple assignments like: ``a, b = 1, 2;``. It also works for returning multiple values.
- If no explicit return value is used for a value, the actual object is returned (return self).
- The ``this`` keyword is actually called ``self``.

Saffire for Python programmers
------------------------------
There are currently no entries.

Saffire for Ruby programmers
----------------------------
There are currently no entries.

:Authors:
   Joshua Thijssen
