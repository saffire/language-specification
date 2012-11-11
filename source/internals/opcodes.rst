#######
Opcodes
#######

Saffire opcode structure is based on Python opcodes, yet they are not compatible. It is not possible to run Saffire's
bytecode on a Python virtual machine and vice versa.


------------------------
Opcodes without operands
------------------------
These opcodes do not take any additional operands.

======     ====================     ==========================================
Opcode     Value                    Description
======     ====================     ==========================================
00h        STOP
01h        POP_TOP
02h        ROT_TWO
03h        ROT_THREE
04h        DUP_TOP
05h        ROT_FOUR
09h        NOP
0Ah        UNARY_POSITIVE
0Bh        UNARY_NEGATIVE
0Ch        UNARY_NOT
0Dh        UNARY_CONVERT
0Fh        UNARY_INVERT
12h        LIST_APPEND
13h        BINARY_POWER
14h        BINARY_MULTIPLY
15h        BINARY_DIVIDE
16h        BINARY_MODULO
17h        BINARY_ADD
18h        BINARY_SUBTRACT
19h        BINARY_SUBSCR
1Ah        BINARY_FLOOR_DIVIDE
1Bh        BINARY_TRUE_DIVIDE
1Ch        INPLACE_FLOOR_DIVIDE
1Dh        INPLACE_TRUE_DIVIDE
1Eh        SLICE
1Fh        SLICE+1
20h        SLICE+2
21h        SLICE+3
28h        STORE_SLICE
29h        STORE_SLICE+1
2Ah        STORE_SLICE+2
2Bh        STORE_SLICE+3
32h        DELETE_SLICE
33h        DELETE_SLICE+1
34h        DELETE_SLICE+2
35h        DELETE_SLICE+3
37h        INPLACE_ADD
38h        INPLACE_SUBTRACT
39h        INPLACE_MULTIPLY
3Ah        INPLACE_DIVIDE
3Bh        INPLACE_MODULO
3Ch        STORE_SUBSCR
3Dh        DELETE_SUBSCR
3Eh        BINARY_LSHIFT
3Fh        BINARY_RSHIFT
40h        BINARY_AND
41h        BINARY_XOR
42h        BINARY_OR
43h        INPLACE_POWER
44h        GET_ITER
4Bh        INPLACE_LSHIFT
4Ch        INPLACE_RSHIFT
4Dh        INPLACE_AND
4Eh        INPLACE_XOR
4Fh        INPLACE_OR
50h        BREAK_LOOP
51h        WITH_CLEANUP
52h        LOAD_LOCALS
53h        RETURN_VALUE
54h        IMPORT_STAR
55h        EXEC_STMT
56h        YIELD_VALUE
57h        POP_BLOCK
58h        END_FINALLY
59h        BUILD_CLASS
======     ====================     ==========================================



----------------------
Opcodes with 1 operand
----------------------
These opcodes all have 1 operand. The opcodes are distinguished from others by looking at the most significant bit.
If that bit is set to 1, it means it has one operand. IN practice, this means **80h** to **BFh** have the highest bit
set. The next opcode **C0h** has the two highest bit set, and is discussed in the `Opcodes with multiple operands`_
section.

======     ====================     ==========================================
Opcode     Value                    Description
======     ====================     ==========================================
80h        STORE_NAME
81h        DELETE_NAME
82h        UNPACK_SEQUENCE
82h        FOR_ITER
5Fh        STORE_ATTR
60h        DELETE_ATTR
61h        STORE_GLOBAL
62h        DELETE_GLOBAL
63h        DUP_TOPX
64h        LOAD_CONST
65h        LOAD_NAME
66h        BUILD_TUPLE
67h        BUILD_LIST
68h        BUILD_MAP
69h        LOAD_ATTR
6Ah        COMPARE_OP
6Bh        IMPORT_NAME
6Ch        IMPORT_FROM
6Eh        JUMP_FORWARD
6Fh        JUMP_IF_FALSE
70h        JUMP_IF_TRUE
71h        JUMP_ABSOLUTE
74h        LOAD_GLOBAL
77h        CONTINUE_LOOP
78h        SETUP_LOOP
79h        SETUP_EXCEPT
7Ah        SETUP_FINALLY
7Ch        LOAD_FAST
7Dh        STORE_FAST
7Eh        DELETE_FAST
82h        RAISE_VARARGS
83h        CALL_FUNCTION
84h        MAKE_FUNCTION
85h        BUILD_SLICE
86h        MAKE_CLOSURE
87h        LOAD_CLOSURE
88h        LOAD_DEREF
89h        STORE_DEREF
8Ch        CALL_FUNCTION_VAR
8Dh        CALL_FUNCTION_KW
8Eh        CALL_FUNCTION_VAR_KW
8Fh        EXTENDED_ARG
======     ====================     ==========================================


------------------------------
Opcodes with multiple operands
------------------------------

For future reservations, opcodes with two or more operands are possible. They consist of having the highest bits set
to 1. In effect this means that operands starting from **C0h** to **DFh** are reserved for opcodes with 2 operands
(since these opcodes have the highest 2 bits set). Opcdoes **E0h** to **EFh** have the highest 3 bits set, so they are
reserved for 3 operand opcodes. **F0h** to **FEh** are reserved for opcodes with 4 operands. Opcode **FFh** has
special meaning and is discussed in the `Reserved opcodes`_ section.

==========      ==============================================================
Opcodes         Description
==========      ==============================================================
C0h to DFh      2 operand codes (reserved for future use)
E0h to EFh      3 operand codes (reserved for future use)
F0h to FEh      4 operand codes (reserved for future use)
==========      ==============================================================


----------------
Reserved opcodes
----------------

======     ====================     ==========================================
Opcode     Value                    Description
======     ====================     ==========================================
FFh        <reserved>               Reserved for future use. Can be used as a marker to indicate special opcode cases.
======     ====================     ==========================================


