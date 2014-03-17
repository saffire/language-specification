=======
Exception
=======

This is the base exception class. Every exception should extend this class. It's not possible to throw an ``exception``
object, or catch an object that is not extended from this ``exception`` class.


Predefined exceptions
---------------------

    * ``systemException``
        * ``indexException``
        * ``attributeException``
        * ``typeException``
        * ``callException``
            * ``argumentException``
            * ``callableException``
            * ``visibilityException``
        * ``importException``
        * ``ooException``
            * ``interfaceException``
            * ``extendException``
    * ``arithmeticException``
        * ``divideByZeroException``
    * ``ioException``
        * ``fileException``
            * ``fileNotFoundException``



Methods
-------

.. method:: exception.getMessage

    Returns the set exception message

.. method:: exception.setMessage(string message)

    Sets the exception message, returns ``self``

.. method:: exception.getCode()

    Returns the set exception code

.. method:: exception.setCode(numerical code)

    Sets the exception code, returns ``self``




Cast methods
************

.. method:: exception.__boolean

    Returns ``boolean(true)``


.. method:: exception.__numerical

    Returns the error code, or ``numerical(0)`` if not set.


.. method:: exception.__string

    Returns the error message, or ``string("")`` if not set.


Operator methods
****************

.. method:: boolean.__cmp_eq()

    The == comparison. Returns ``true`` when the exceptions are equal


.. method:: boolean.__cmp_ne()

   The != comparison. Returns ``true`` when the exceptions are not equal




