#############
Using Saffire
#############

Command line usage
------------------
Saffire can be run easily from the commandline.

Usage: saffire [options] [script [args]]

Help
----
Returns help information about saffire and its command.


::

     saffire help <command>

Version
-------
Returns version information.

--long
   Return more detailed information, including compile time, and configure flags.


Lint
----
Do a syntax check on specified source file. Returns exitcode 0 when the file is syntax correct.

Repl
----
This function is not yet implemented.

FastCGI
-------
This function is not yet documented.

Config
------
View or edit the saffire configuration files

::

     saffire config list

Displays the whole configuration list

::

     saffire config search <keyword>

Lists all the configuration settings based on keyword

::

     saffire config set <key> <value>

Sets the configuration key to value.


--global
    Uses the global saffire configuration instead of your local one.



Exec
----
Running

::

     saffire exec <file.sf>

will compile and run the given file. If there is a pre-compiled file **file.sfc**
present, this file will be used instead of recompiling the source file. However, if the source file has changed after
the compilation (as detected by a change in the timestamp of the source file), it will recompile the bytecode file.

It is also possible to execute compiled files directly by specifying **file.sfc**.



Bytecode
--------
The bytecode command allows you to deal with Saffire code turned into bytecode. This bytecode is the actual code run by
the Saffire virtual machine (VM). It's possible to run a Saffire application directly from the bytecode without the use
of the actual source code.

bytecode compile
================
This will compile a saffire source file into a sfc bytecode file.

--text
   Generate an assembly file for this bytecode. This file will be generated as **<file>.sfa**
--dot
   Generate a DOT file for visualizing the bytecode's AST. This file will be generated as **<file>.dot**
--sign
   Sign the bytecode.
--no-sign
   Do not sign the bytecode.
--key <key>
   Use <key> for signing the bytecode.

bytecode sign
=============
Sign an unsigned file with your private key

--key <key>
   Use <key> for signing the bytecode.

bytecode unsign
===============
Strip the signing of a bytecode signed file

bytecode info
=============
Returns information about the specified bytecode file


:Authors:
   Joshua Thijssen
   Caspar Dunant
