====
Base
====

The ``base`` class is the class that will be ultimately extended. Every class inside Saffire will be either be extended
from another class, or if no other class is specified, will be extended from the ``base``.

This means that the following are identical:

::

    class foo { }

::

    class foo extends base { }



Methods
-------

*   base.__new()

    Called when instantiating a class. This method cannot be called directly.

*   base.__ctor()

    Called when instantiating a class. This method cannot be called directly.

*   base.__dtor()

    Called when destroying an instance . This method cannot be called directly.

*   base.__properties()

    Returns a ``hash`` of all the properties of the given instance.

    ::

        f = base();
        props = f.__properties();     // hash[];

        f.a = 1;
        props = f.__properties();     // hash['a' => 1];

        f.b = 1;
        props = f.__properties();     // hash['a': 1, 'b': 2];



*   base.__methods()

    Returns a ``hash`` of all the methods of the given instance.

    ::

        f = base();
        methods = f.__methods();     // hash[];

        f.a = 1;
        methods = f.properties();     // hash['a' => 1];

        f.b = 1;
        methods = f.properties();     // hash['a': 1, 'b': 2];



*   base.__parents()

    Returns a ``list`` of all the parents of the given instance.

    ::

        f = base();
        parents = f.__parents();        // list[]


        s = "foo";
        parents = s.__parents();        // list['base']

        class foo { }
        class bar extends foo { }
        class baz extends bar { }

        b = baz();
        parents = b.__parents();        // list['bar', 'foo', 'base']



*   base.__name()

    Returns the name of the class.

    ::

        import io;

        s = "foo";
        io.print(s.__name());       // "string"

        class foo { }
        class bar extends foo { }

        b = bar();
        io.print(b.__name());       // "bar"


*   base.__implements()

    Returns a ``list`` of all the interfaces the instance implements.

    ::

        import io;

        s = "foo";
        io.print(s.__implements());     // list['datastructure', 'iterator', 'subscript'];


*   base.__memory()

    Returns the memory usage of the instance.

*   base.__annotations()

    Returns a list of all annotations.

    .. warning::
	    Annotations are not yet implemented into the Saffire language.


    ::

        @myannotation("an1")
        class foo {

            @anotherannotation(k1 : "an2", k2 : 3)
            public method bar() {
            }

            @cache
            public method baz() {
            }
        }

        foo.__annotations();

        /*
        hash[[
            'class' => hash[[
                'myannotation' : hash[['value': "an1"]]
            ]],
            'methods' : hash[[
                'bar' : hash[[
                    hash[[
                        'anotherannotation' : hash[['k1': "an2"]],
                    ]],
                ]],
                'baz' : hash[[
                    hash[[
                        'cache' : hash[[ ]],
                    ]],
                ]],
            ]],
            'properties' : hash[[
            ]]
        ]];
        */


*   base.__clone()

    Clones the instance into a new instance. Creates an exact replica.

    ::

        import io;

        f = base();
        f.a = 1;

        g = f;
        h = f.clone();

        f.a = 2;
        io.print(f.a);      // 2
        io.print(g.a);      // 2, as f and g are the same reference
        io.print(h.a);      // 1, as f and h are different objects


*   base.__immutable?()

    Returns ``true`` when the instance cannot be changed (no properties can be changed). ``false`` otherwise.

    ::

        import io;

        f = base();
        io.print(f.__immutable?());   // Returns false

        f.__immutable();
        io.print(f.__immutable?());   // Returns true


*   base.__immutable()

    Sets the instance to immutable. No more changes can be made to its properties. Once immutable, the isntance cannot
    be set mutable again.

    ::

        f = base();
        f.a = 1;
        f.__immutable();
        f.a = 2;            // will throw exception

*   base.__destroy()

    Destroy the instance.

    ::

        a = "foo";
        a.__destroy();

        a.__id();       // throw exception, as 'a' is not declared anymore.

*   base.__refcount()

    Returns the number of times this instance is referenced.

    ::

        import io;

        class foo { }

        a = foo();
        io.print(a.__refcount());       // 1

        b = a;
        io.print(a.__refcount());       // 2
        io.print(b.__refcount());       // 2

        b = 1;
        io.print(a.__refcount());       // 1



*   base.__id()

    Returns a unique identifier for this instance.

    ::

        import io;

        a = base();
        b = a;
        c = a.__clone();
        io.print(a.__id());     // 0x1851515        // or any other random number
        io.print(b.__id());     // 0x1851515        // same as a.__id(), as they are the same instance
        io.print(c.__id());     // 0x8034623        // another instance (cloned), thus another __id()

