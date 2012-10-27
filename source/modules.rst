#######
Modules
#######
Modules can be seen as "directories". Each directory is a module that consists of files or other directories. Those
directories are modules too.

There are two ways to use modules.

- Import classes from modules into the current namespace
- Use a fully-qualified name or alias to the class inside the module


Import classes
--------------
Importing classes into the current namespace can be very helpful when you need to use those classes very frequently.
Instead of having to use an alias or fully qualified name to the class, you can consider the class as part of the
current namespace, so you can access them directly.

::

    import io from io;
    io.print("hello world");

This example imports the "io" class from the "io" module into the current namespace. Note that this means that you
cannot have another class named "io" inside the same namespace:

::

    import io from io;

    class io {  // Incorrect.
    }

It's common practice to have a class with the same name as the module inside the module. In that case, you can omit
the "from" part:

::

    import io;  // Implies: import io from io;
    io.print("hello world");

It's also possible to "alias" the class name into the current namespace:

::

    import io as foo;
    foo.print("hello world");

.. note::
    the classname() method that returns the name of the current class will ALWAYS return the actual name, not the
    aliased name. There is no functionality to find out an aliased name.

All options are possible too:

::

    import io from io as std_io;
    import console from io as std_console;
    std_console.print("hello world");


Fully qualified names or aliasing
---------------------------------
Since importing classes can create namespace pollution, it's always possible to reference classes from outside by using
their fully qualified name. You must however, declare that you will be using those namespaces with the "use" statement.

::

    use io;
    io::io.print("hello world");

Again, it's possible to alias such a namespace:

::

    use io as my_io;
    my_io::io.print("hello world");

Because we do not import any classes into the current namespace, the following will work:

::

    use io;

    class io { ... }

    // Calls the print method from our class
    io.print("hello world");

    // Calls the print method from the io class from the io module.
    io::io.print("hello world");


It's also possible to alias our namespaces if needed:

::

    use framework::http::request as request;
    use framework::http::response as response;

    $req = request::request();
    $rsp = response::response();
    if ($req.method == "GET") {
        $rsp.code = 405;
        $rsp.message = "Method not allowed";
    }

It's even possible to alias one namespace to multiple aliases:

::

    use io as foo;
    use io as bar;

    foo::io.print("Hello");
    bar::io.print("Hello");


:Authors:
   Joshua Thijssen
