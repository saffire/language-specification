=========
Numerical
=========

The ``numerical`` class represents any (64bit) integer. This number can range from ``-9,223,372,036,854,775,808`` to
``9,223,372,036,854,775,807``. These numbers are also defined as ``Numerical.MIN`` and ``Numerical.MAX`` constants.

For other numerical types, see the `Decimal`_ and the `Complex`_ classes.


::

    import io;

    i = 1;
    j = 2;
    io.print (i + j);   // 3


.. attention::
	Be careful when dealing with large (or small) numbers. If you overflow or underflow a numerical value, it will throw
	an exception.

	::

	    i = Numerical.MAX - 100;
	    i += 50;                    // ok, still in range of Numerical
	    i += 151;                   // Throws exception, as we overflowed the Numerical.


Constants
---------

.. data:: numerical.MIN

    The lowest number the Numerical class is capable of handling.

.. data:: numerical.MAX

    The highest number the Numerical class is capable of handling.

Methods
-------

.. method:: numerical.neg()

    Negate a numerical.

    ::

        i = 1.neg();        // i = -1
        i = -4.neg();       // i = 4


.. method:: numerical.abs()

    Returns the absolute value of a numerical


Cast methods
************


.. method:: numerical.__boolean()

    Converts a numerical to a boolean. Will return ``false`` when the numerical is ``0``. ``true`` otherwise.

    ::

        1.__boolean();      // true
        0.__boolean();      // false
        -1.__boolean();     // true


.. method:: numerical.__string()

    Converts a numerical to a string.

    ::

        1.__string();                   // "1"
        0.__string();                   // "0"
        -1.__string();                  // "-1"
        Numerical.MIN.__string();       // "-9223372036854775808"



Operator methods
****************


.. method:: numerical.__opr_add()

    The + operator. Adds two numericals.

    ::

        return 1 + 4;       // 5


.. method:: numerical.__opr_sub()

    The - operator. Subtracts two numericals.

    ::

        return 1 - 4;       // -3


.. method:: numerical.__opr_mul()

    The * operator. Multiplies two numericals.

    ::

        return 2 * 8;       // 16


.. method:: numerical.__opr_div()

    The * operator. divides two numericals. If dividing by 0, it will throw an ``DivideByZeroException``. If the division
    is not a whole number, it will return a ``Decimal``, otherwise it will return a ``Numerical``.

    ::

        return 8 / 4;       // Numerical(2)
        return 10 / 4;       // Double(2.5)
        return 9 / 3;       // Double(3.333333)


.. method:: numerical.__opr_mod()

    The % operator. Returns the modulus of two numericals.

    ::

        return 8 % 4;       // Numerical(0)
        return 9 % 4;       // Numerical(1)
        return 2 % 4;       // Numerical(2)


.. method:: numerical.__opr_and()

    The & bitwise operator. Returns the bitwise AND of two numericals.

    ::

        return 1 & 5;       // Numerical(5)
        return 9 & 4;       // Numerical(0)
        return 15 & 4;       // Numerical(4)


.. method:: numerical.__opr_or()

    The | bitwise operator. Returns the bitwise OR of two numericals.

    ::

        return 1 | 4;       // Numerical(5)
        return 9 | 4;       // Numerical(13)
        return 15 | 4;      // Numerical(15)


.. method:: numerical.__opr_xor()

    The ^ bitwise operator. Returns the bitwise XOR of two numericals.

    ::

        return 1 | 4;       // Numerical(5)
        return 9 | 4;       // Numerical(13)
        return 15 | 4;      // Numerical(11)
        return 7 | 7;       // Numerical(0)


.. method:: numerical.__opr_shl()

    The << bitwise operator. Shifts the bits to the left a number of times. Will pad with 0's

    .. warning::
	    This operator does not take into account the sign of the numerical.

    ::

        return 5 << 2;       // Numerical(20)
        return 9 << 4;       // Numerical(144)
        return 15 << 4;      // Numerical(240)
        return 7 << 7;       // Numerical(896)


.. method:: numerical.__opr_shr()

    The >> bitwise operator. Shifts the bits to the right a number of times. Will pad with 0's

    .. warning::
	    This operator does not take into account the sign of the numerical.


    ::

        return 5 << 2;       // Numerical(20)
        return 9 << 4;       // Numerical(144)
        return 15 << 4;      // Numerical(240)
        return 7 << 7;       // Numerical(896)



Comparison methods
******************



.. method:: numerical.__cmp_eq()

    The == comparison. Returns ``true`` when both numerical values are equal.

    ::

        if ( 5 == 5) { }        // true


.. method:: numerical.__cmp_ne()

    The != comparison. Returns ``true`` when both numerical values are **not** equal.

    ::

        if ( 1 != 5) { }        // true
        if ( 5 != 5) { }        // false



.. method:: numerical.__cmp_lt()

    The < comparison. Returns ``true`` when the first numerical is less than the second.

    ::

        if ( 1 < 5) { }        // true
        if ( 5 < 1) { }        // false
        if ( 1 < 1) { }        // false


.. method:: numerical.__cmp_gt()

    The > comparison. Returns ``true`` when the first numerical is greater than the second.

    ::

        if ( 1 > 5) { }        // false
        if ( 5 > 1) { }        // true
        if ( 1 > 1) { }        // false


.. method:: numerical.__cmp_le()

    The <= comparison. Returns ``true`` when the first numerical is greater or equal as the second.

    ::

        if ( 1 <= 5) { }        // true
        if ( 5 <= 1) { }        // false
        if ( 1 <= 1) { }        // true


.. method:: numerical.__cmp_ge()

    The >= comparison. Returns ``true`` when the first numerical is less or equal as the second.

    ::

        if ( 1 >= 5) { }        // false
        if ( 5 >= 1) { }        // true
        if ( 1 >= 1) { }        // true
