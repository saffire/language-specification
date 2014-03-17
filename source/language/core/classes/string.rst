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



Methods
-------

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


.. method:: string.dup(Numerical times = 1)

    Duplicates the string multiple times.

    ::

        "foo".dup();        // "foofoo"
        "foo".dup(2);       // "foofoofoo"



Cast methods
************

.. method:: boolean.__numerical

    Returns a numerical representation of the boolean. This can be either a 1 when true, or 0 when false.


.. method:: boolean.__string

    Returns a string representation of the boolean. This can be either ``string("true")`` or ``string("false")``.



Operator methods
****************

.. method:: string.__opr_add()

    The + operator. Adds two booleans.

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



Comparison methods
******************


.. method:: string.__cmp_eq()

    The == comparison. Returns ``true`` when both strings values are equal. Note that they do not have to be the exact
    same reference. The comparison

    ::

        if ( "foo" == "foo") { }        // true
        if ( "foo" == "bar") { }        // false


.. method:: string.__cmp_ne()

    The != comparison. Returns ``true`` when both string values are **not** equal.

    ::

        if ( "foo" != "bar") { }           // true
        if ( "foo" != "foo".upper()) { }   // true



.. method:: string.__cmp_lt()

    The < comparison. Returns ``true`` when the first string is less than the second string. The comparison is done
    through standard string compare, in the string's collation.

    As taken from the ICU documentation:

    * The letters A-Z can be sorted in a different order than in English. For example, in Lithuanian, "y" is sorted between "i" and "k".
    * Accented letters can be treated as distinct letters. For example, "Å" in Danish is treated as a separate letter that sorts just after "Z".


.. method:: string.__cmp_gt()

    The > comparison. Returns ``true`` when the first string is greater than the second.



.. method:: string.__cmp_le()

    The <= comparison. Returns ``true`` when the first string is greater or equal as the second.


.. method:: string.__cmp_ge()

    The >= comparison. Returns ``true`` when the first string is less or equal as the second.



.. method:: string.__cmp_in()

    The 'in' comparison. Returns ``true`` when the first string can be found inside the second string.

    ::

        if ("foo" in "foobar") { }      // true

        if ("o" in "foobar") { }        // true

        if ("x" in "foobar") { }        // false


.. method:: string.__cmp_ni()

    The 'not in' comparison. Returns ``true`` when the first string cannot be found inside the second string.

    ::

        if ("foo" not in "foobar") { }   // false

        if ("o" not in "foobar") { }     // false

        if ("x" not in "foobar") { }     // true

