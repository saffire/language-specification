#########
Internals
#########

Saffire's internal structure is heavily based on the code of Python. This is for two reasons. First, because of the two
main languages we "adapt", the Python's internal structure is the most sane one. Secondly, we quickly came to the
conclusion that lot of idea's we are having, are - in some form or the other - already implement similar in the Python
language. One of the main idea's, working with abstract objects (t_*_object), is quite similar to python's object
structure (PyObject_*). Even though we do a lot of research in both Python and PHP's cores, we simply do not want to
copy everything over 1:1. Afteral, Saffire aims to be a complement to both Python and PHP, and not merely a copy.


.. toctree::
   :maxdepth: 2

   opcodes


:Authors:
   Joshua Thijssen
