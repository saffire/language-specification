======
String
======

The ``string`` class represents a serie of bytes. They can be seen as text, but could as well be binary data. The
``string`` class is binary safe and can hold up to 2^64 bytes.




::

    import io;

    s = "foo";
    io.print(s);                            // "foo"

    io.print(s.upper());                    // "FOO"
    io.print("bar".reverse().upper());      // "RAB"


Constants
---------

.. data:: string.PAD_LEFT

    See `string.pad`_

.. data:: string.PAD_RIGHT

    See `string.pad`_

.. data:: string.PAD_BOTH

    See `string.pad`_

.. data:: string.TRIM_LEFT

    See `string.trim`_

.. data:: string.TRIM_RIGHT

    See `string.trim`_

.. data:: string.TRIM_BOTH

    See `string.trim`_


Methods
-------

.. method:: string.length()

    Returns the length of the string in the number of characters based on the conversion used. If the conversion is
    standard ``BYTE``, every byte equals one character and thus ``length()`` and ``byte_length()`` are always equal.
    However, when the conversion is set to ``UTF-8``, the ``byte_length()`` can differ from the ``length()`` if there
    are characters that are based on multiple bytes.

    ::

        "foo".length()            // 3
        "Bjšrk".length()          // 6 (based on the default utf8 conversion)
        "Bjšrk".utf8().length()   // 5
        "Bjšrk".utf16().length()  // 5


.. method:: string.byte_length()

    Returns the length of the string in bytes, based on the conversion used

    ::

        "foo".byte_length()              // 3
        "Bjšrk".byte_length()            // 6
        "Bjšrk".byte_length()            // 6 (5x utf8, from which the š consists 2 bytes)
        "Bjšrk".utf16().byte_length()    // 10 bytes (5x utf16)


.. method:: string.upper()

    Returns a string with all characters uppercased (based on the conversion and locale used)

    ::

        "foo".upper()     // "FOO"


.. method:: string.lower()

    Returns a string with all characters lowercased (based on the conversion and locale used)

    ::

        "FOO".upper()     // "foo"


.. method:: string.reverse()

    Reverse a string with all characters lowercased (based on the conversion and locale used)

    ::

        "FOO".upper()     // "foo"


.. method:: string.toLocale()

    Negate a numerical.

    ::

        i = 1.neg();        // i = -1
        i = -4.neg();       // i = 4


.. method:: string.setLocale()

    Negate a numerical.

    ::

        i = 1.neg();        // i = -1
        i = -4.neg();       // i = 4



.. method:: string.splice()

    Negate a numerical.

    ::

        i = 1.neg();        // i = -1
        i = -4.neg();       // i = 4





.. method:: string.__boolean()

    Converts a numerical to a boolean. Will return ``false`` when the numerical is ``0``. ``true`` otherwise.

    ::

        1.__boolean();      // true
        0.__boolean();      // false
        -1.__boolean();     // true


.. method:: string.__numerical()

    Converts a numerical to a string.

    ::

        1.__string();                   // "1"
        0.__string();                   // "0"
        -1.__string();                  // "-1"
        Numerical.MIN.__string();       // "-9223372036854775808"


.. method:: string.__opr_add()

    The + operator. Adds two numericals.

    ::

        return 1 + 4;       // 5


.. method:: string.__opr_sub()

    The - operator. Subtracts two numericals.

    ::

        return 1 - 4;       // -3


.. method:: string.__opr_mul()

    The * operator. Multiplies two numericals.

    ::

        return 2 * 8;       // 16


.. method:: string.__opr_div()

    The * operator. divides two numericals. If dividing by 0, it will throw an ``DivideByZeroException``. If the division
    is not a whole number, it will return a ``Decimal``, otherwise it will return a ``Numerical``.

    ::

        return 8 / 4;       // Numerical(2)
        return 10 / 4;       // Double(2.5)
        return 9 / 3;       // Double(3.333333)


.. method:: string.__opr_mod()

    The % operator. Returns the modulus of two numericals.

    ::

        return 8 % 4;       // Numerical(0)
        return 9 % 4;       // Numerical(1)
        return 2 % 4;       // Numerical(2)


.. method:: string.__opr_and()

    The & bitwise operator. Returns the bitwise AND of two numericals.

    ::

        return 1 & 5;       // Numerical(5)
        return 9 & 4;       // Numerical(0)
        return 15 & 4;       // Numerical(4)


.. method:: string.__opr_or()

    The | bitwise operator. Returns the bitwise OR of two numericals.

    ::

        return 1 | 4;       // Numerical(5)
        return 9 | 4;       // Numerical(13)
        return 15 | 4;      // Numerical(15)


.. method:: string.__opr_xor()

    The ^ bitwise operator. Returns the bitwise XOR of two numericals.

    ::

        return 1 | 4;       // Numerical(5)
        return 9 | 4;       // Numerical(13)
        return 15 | 4;      // Numerical(11)
        return 7 | 7;       // Numerical(0)



.. method:: string.__cmp_eq()

    The == comparison. Returns ``true`` when both numerical values are equal.

    ::

        if ( 5 == 5) { }        // true


.. method:: string.__cmp_ne()

    The != comparison. Returns ``true`` when both numerical values are **not** equal.

    ::

        if ( 1 != 5) { }        // true
        if ( 5 != 5) { }        // false



.. method:: string.__cmp_lt()

    The < comparison. Returns ``true`` when the first numerical is less than the second.

    ::

        if ( 1 < 5) { }        // true
        if ( 5 < 1) { }        // false
        if ( 1 < 1) { }        // false


.. method:: string.__cmp_gt()

    The > comparison. Returns ``true`` when the first numerical is greater than the second.

    ::

        if ( 1 > 5) { }        // false
        if ( 5 > 1) { }        // true
        if ( 1 > 1) { }        // false


.. method:: string.__cmp_le()

    The <= comparison. Returns ``true`` when the first numerical is greater or equal as the second.

    ::

        if ( 1 <= 5) { }        // true
        if ( 5 <= 1) { }        // false
        if ( 1 <= 1) { }        // true


.. method:: string.__cmp_ge()

    The >= comparison. Returns ``true`` when the first numerical is less or equal as the second.

    ::

        if ( 1 >= 5) { }        // false
        if ( 5 >= 1) { }        // true
        if ( 1 >= 1) { }        // true


.. method:: string.__cmp_in()

    The >= comparison. Returns ``true`` when the first numerical is less or equal as the second.

    ::

        if ( 1 >= 5) { }        // false
        if ( 5 >= 1) { }        // true
        if ( 1 >= 1) { }        // true


.. method:: string.__cmp_ni()

    The >= comparison. Returns ``true`` when the first numerical is less or equal as the second.

    ::

        if ( 1 >= 5) { }        // false
        if ( 5 >= 1) { }        // true
        if ( 1 >= 1) { }        // true


.. warning::
	The following methods are not yet implemented.



.. method:: string.pad(numerical width, numerical direction = String.PAD_RIGHT, string padding_character = " ")

    width
        The width on which the string must be padded. If the string is larger, no padding will occur and
        the string will be returned as-is.
    direction
        The direction in which padding will occur and can be one of the following constants:

            - PAD_LEFT
                Pad to the left
            - PAD_RIGHT
                Pad to the right
            - PAD_BOTH
                Pad both to the left and right to center the string. Note that when padding is odd, the left
                side will be padded with 1 more element.

    padding_character
        The actual string to pad. ``pad()`` can pad with strings with more than one character. If the
        padding does not match up to ``width``, it will truncate the padding string accordingly.


    ::

        import io;

        io.print("foo".pad(20));                            // "foo                 "
        io.print("foo".pad(20, string.PAD_RIGHT));          // "                 foo"

        io.print("foo".pad(20, string.PAD_BOTH));           // "        foo         "
        io.print("foo".pad(20, string.PAD_BOTH, "abc"));    // "abcabcabfooabcabcabc"

        io.print("foobar".pad(2));                          // "foobar"


.. method:: string.utf8()

    This method is a shortcut for convert("utf-8")

.. method:: string.utf16()

    This method is a shortcut for convert("utf-16")

.. method:: string.convert(string charset)

    Convert the string to the specified character set.

.. method:: string.byte_length()

    Returns number of BYTES in this string (which can be more than actual characters)

.. method:: string.char_length()

    Alias for string.lenght()

.. method:: string.isNumerical()

    Returns ``true`` when the full string contains a numerical value. ``false`` otherwise.

    ::

        "1".isNumerical();      // true
        "1test".isNumerical();  // false
        "".isNumerical();       // false
        "zero".isNumerical();   // false
        "-124".isNumerical();   // true


.. method:: string.isHex()

    Returns ``true`` when the full string contains a hexadecimal value. ``false`` otherwise. Note that this value does
    not neccesarily can be converted to a numerical, as the hex-string might be larger than a numerical could fit.

    ::

        "1231".isHex();     // true
        "1a".isHex();       // true
        "1A".isHex();       // true
        "0xA".isHex();      // false    ('x' is not a valid hex character)

.. method:: string.isAlpha()

    Returns ``true`` when the string contains alphabet values (A-Z and a-z)

.. method:: string.isAlphaNum()

    Returns ``true`` when the string contains alphanumericals values (A-Z and a-z and 0-9)

.. method:: string.isLower()

    Returns ``true`` when the string contains only lowercase characters, and ONLY alpha characters.

    ::

        "foo".isLower()         // true
        "fOO".isLower()         // false
        "1234abcd".isLower()    // false, 1234 are not validad characters

.. method:: string.isSpace()

    Returns ``true`` when the string contains only space characters (\t \n \r [space] etc)

.. method:: string.isUpper()

    Returns ``true`` when the string contains only uppercase characters, and ONLY alpha characters.

    ::

        "foo".isLower()         // false
        "FOO".isLower()         // true
        "1234ABCD".isLower()    // false, 1234 are not valid characters


.. method:: string.capitalize()

    Capitalize string. Every word will start with a uppercase character. All other characters will be lower case.

    ::

        "hello, this iS a TEST".capitalize(); // "Hello, This Is A Test"


.. method:: string.replace(string old, string new)

    Replaces part of the string with another string

    ::

        "foobarbar".replace("bar", "test", 1);      // "footesttest"


.. method:: string.replace(string old, string new, numerical count)

    Replaces part of the string with another string, but at maximum of ``count`` times.

    ::

        "foobarbar".replace("bar", "test", 1);      // "footestbar"

.. method:: string.split(string old, numerical max)

.. method:: string.trim(string charlist, directory = string.TRIM_RIGHT)

.. method:: string.startsWith(string prefix, boolean ignoreCase = false)

    Returns ``true`` when the string starts with ``prefix``. When ``ignoreCase`` is true, it will check case insensitive.

.. method:: string.endsWith(string postfix, boolean ignoreCase = false)

    Returns ``true`` when the string ends with ``postfix``. When ``ignoreCase`` is true, it will check case insensitive.

.. method:: string.match(Regex re)

    Matches the string against the regular expression. Returns ``true`` when the regex matches

.. method:: string.format()

.. method:: string.substring()

    Alias for `string.splice`_

