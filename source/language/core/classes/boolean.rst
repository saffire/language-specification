=======
Boolean
=======

The ``boolean`` class represents a boolean value. There are only two instances that can be created from the boolean
class: ``true`` and ``false``.

.. attention::
    It's not possible to instantiate the boolean class directly. You must use either the ``true`` or ``false``
    instances instead.

.. attention::
    It's not possible to extend this class.



Methods
-------


Operator methods
****************


.. method:: boolean.__opr_add()

    The ``+`` operator. Adds two booleans.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |    true    |
    +------------+------------+------------+
    |    true    |   false    |    true    |
    +------------+------------+------------+
    |    true    |    true    |    true    |
    +------------+------------+------------+


    ::

        a = true + false;       // true
        a = false + false;      // false
        a = (1 < 0) + (3 < 2);  // false




.. method:: boolean.__opr_sub()

    The ``-`` operator. Subtracts two booleans.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |   false    |
    +------------+------------+------------+
    |    true    |   false    |    true    |
    +------------+------------+------------+
    |    true    |    true    |   false    |
    +------------+------------+------------+


.. method:: boolean.__opr_mul()

    The ``*`` operator. Multiplies two booleans.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |   false    |
    +------------+------------+------------+
    |    true    |   false    |   false    |
    +------------+------------+------------+
    |    true    |    true    |    true    |
    +------------+------------+------------+




.. method:: boolean.__opr_div()

    The ``/`` operator. Divides two booleans.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |   false    |
    +------------+------------+------------+
    |    true    |   false    |   false    |
    +------------+------------+------------+
    |    true    |    true    |    true    |
    +------------+------------+------------+


.. method:: boolean.__opr_mod()

    The ``%`` operator. Modulus two booleans.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |   false    |
    +------------+------------+------------+
    |    true    |   false    |   false    |
    +------------+------------+------------+
    |    true    |    true    |    true    |
    +------------+------------+------------+


.. method:: boolean.__opr_and()

    The bitwise ``&`` operator. ANDs two booleans.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |   false    |
    +------------+------------+------------+
    |    true    |   false    |   false    |
    +------------+------------+------------+
    |    true    |    true    |    true    |
    +------------+------------+------------+

.. method:: boolean.__opr_or()

    The bitwise ``|`` operator. ORs two booleans.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |    true    |
    +------------+------------+------------+
    |    true    |   false    |    true    |
    +------------+------------+------------+
    |    true    |    true    |    true    |
    +------------+------------+------------+

.. method:: boolean.__opr_xor()

    The bitwise ``^`` operator. XORs two booleans.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |    true    |
    +------------+------------+------------+
    |    true    |   false    |    true    |
    +------------+------------+------------+
    |    true    |    true    |   false    |
    +------------+------------+------------+



.. method:: boolean.__opr_sl()

    The shiftleft ``<<`` operator.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |    true    |
    +------------+------------+------------+
    |    true    |   false    |    true    |
    +------------+------------+------------+
    |    true    |    true    |    true    |
    +------------+------------+------------+


.. method:: boolean.__opr_sr()

    The shiftleft ``>>`` operator.

    +------------+------------+------------+
    | Operand 1  | Operand 2  | Result     |
    +============+============+============+
    |   false    |   false    |   false    |
    +------------+------------+------------+
    |   false    |    true    |    true    |
    +------------+------------+------------+
    |    true    |   false    |    true    |
    +------------+------------+------------+
    |    true    |    true    |    true    |
    +------------+------------+------------+


Comparison methods
******************

.. method:: boolean.__cmp_eq()

    The == comparison. Returns ``true`` when both numerical values are equal.

    ::

        if ( 5 == 5) { }        // true


.. method:: boolean.__cmp_ne()

    The != comparison. Returns ``true`` when both numerical values are **not** equal.

    ::

        if ( 1 != 5) { }        // true
        if ( 5 != 5) { }        // false



.. method:: boolean.__cmp_lt()

    The < comparison. Returns ``true`` when the first numerical is less than the second.

    ::

        if ( 1 < 5) { }        // true
        if ( 5 < 1) { }        // false
        if ( 1 < 1) { }        // false


.. method:: boolean.__cmp_gt()

    The > comparison. Returns ``true`` when the first numerical is greater than the second.

    ::

        if ( 1 > 5) { }        // false
        if ( 5 > 1) { }        // true
        if ( 1 > 1) { }        // false


.. method:: boolean.__cmp_le()

    The <= comparison. Returns ``true`` when the first numerical is greater or equal as the second.

    ::

        if ( 1 <= 5) { }        // true
        if ( 5 <= 1) { }        // false
        if ( 1 <= 1) { }        // true


.. method:: boolean.__cmp_ge()

    The >= comparison. Returns ``true`` when the first numerical is less or equal as the second.

    ::

        if ( 1 >= 5) { }        // false
        if ( 5 >= 1) { }        // true
        if ( 1 >= 1) { }        // true
