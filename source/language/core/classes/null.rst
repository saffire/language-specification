=======
Null
=======

This class represents a "null" value.


.. attention::
    The class cannot be instantiated. You must use the ``null`` instance.

.. attention::
    It's not possible to extend this class.



Methods
-------

Cast methods
************

.. method:: null.__numerical

    Returns ``numerical(0)``


.. method:: null.__string

    Returns ``string(null)``

.. method:: null.__boolean

    Returns ``boolean(false)``





Comparison methods
******************

.. method:: null.__cmp_ne()

    The != comparison. Returns ``true`` when the object is not a ``null``.

    ::

        if ( null != null) { }     // false

        a = 5;
        if ( a != null) { }        // true


