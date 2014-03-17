=======
Hash
=======


The ``hash`` class implements the `iterator`_, `datastructure`_ and `subscription`_  interface.

Methods
-------

.. method:: hash.__ctor

    Constructor

.. method:: hash.__dtor

    Destructor


Cast methods
************

.. method:: hash.__numerical

    Returns a numerical of the hash length.

    ::

        h = hash[[ a:1, b:2, c:3 ]];
        l = hash.__numerical();         // numerical(3)


.. method:: hash.__string

    Returns a string representation of the hash in the form of ``string(hash[length])``.

.. method:: hash.__boolean

    Returns ``true`` when the hash is not empty, false otherwise.


    ::

        if ( hash[[]] ) { }         // false

        if ( hash[[ 1:2 ]]) { }     // true



Operator methods
****************



Comparison methods
******************

