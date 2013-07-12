#######
Opcodes
#######

Saffire opcode structure is based on Python opcodes, yet they are not compatible. It is not possible to run Saffire's
bytecode on a Python virtual machine and vice versa.

------------------
Reading the tables
------------------
Each table has 3 values, the opcode hexidecimal number, the name of the opcode and it's description. The description is
short and uses a few abbreviations:

IP
    The instruction pointer. It is always between 0 and the size of the current codeblock and points to the next
    opcode that is currently being executed.
SP
    Stackpointer. Points to the last stored value on the value-stack. Since stacks grow downwards, SP-0 points to the
    current value, SP-1 points to the previous stored value etc. A stack pointer is always between the current codeblock
    stack-size and 0.
Push
    Adds an object onto the stack (thus **decreasing** the stack pointer). Adding objects onto a full stack will result
    in an error.
Pop
    Removes an object from the stack (thus **increasing** the stack pointer). Popping object from an empty stack will
    result in an error.
OP
    Operand. OP+0 means it's the first operand OP+1 the second etc. An operator is a 2 byte numerical value ranging from
    0x0000 to 0xFFFF
vars
    A table that contains objects that are currently used. Each codeblock has a local vars table and a pointer to the
    global scope vars table.
names
    A table which holds all the names of the variables used in the codeblock. Starts at index 0.
const
    A table which holds objects that are used in the codeblock. Starts at index 0.



------------------------
Opcodes without operands
------------------------
These opcodes do not take any additional operands.

======     ====================     ==========================================
Opcode     Value                    Description
======     ====================     ==========================================
0x00       STOP                     Will end the VM execution.

0x01       POP_TOP                  Removes (pops) SP-0
0x02       ROT_TWO                  Rotates (or swaps) SP-0 with SP-1.
0x03       ROT_THREE                Rotates the last three items on the stack, SP-0 becoming SP-2.
0x04       DUP_TOP                  Duplicates SP-0 and pushes it onto the stack SP-0 and SP-1 wil be equal.
0x05       ROT_FOUR                 Rotates the last four items on the stack SP-0 becoming SP-3.

0x09       NOP                      No operation.

0x72       POP_BLOCK                Removes a block from the frame-stack.
0x73       RETURN                   Returns to the caller frame (or exists when we are at the last frame). SP-0 should
                                    hold an object that is returned. Last frame will need a castable to numerical (or numerical) object that will be the exitcode of the saffire script run.
0x74       BREAK_LOOP               Terminates a loop and continues with the instruction after the loop.
0x75       BREAKELSE_LOOP           Terminates a loop and continues with the else-part of the compound statement.

0x7A       END_FINALLY              Terminates a finally block.
0x7E       USE
0x7F       IMPORT                   Imports class SP-0 from SP-1 and pushes it into the stack
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
80h        STORE_ID                 Stores SP-0 into a variable. The name of the var is found in names[OP+0]. Can be
81h        LOAD_CONST               Create const[OP+0] object and push onto the stack.
82h        LOAD_ID                  Loads identifier(vars[OP+0]) and push onto the stack. Identifier can be local,
                                    global or builtin.

83h        JUMP_FORWARD             The IP will be increased with OP+0.
84h        JUMP_IF_FALSE            if SP-0 cast to boolean returns false, it will increase IP with OP+0.
85h        JUMP_IF_TRUE             if SP-0 cast to boolean returns true, it will increase IP with OP+0.
86h        JUMP_ABSOLUTE            IP will be set to OP+0.

87h        DUP_TOPX                 Duplicate SP-0 OP+0 times onto the stack. DUP_TOP is equal to DUP_TOPX[1].

88h        LOAD_GLOBAL              Loads global identifier(vars[OP+0]) and pushes onto the stack.
89h        STORE_GLOBAL             Stores SP-0 into a global identifier(vars[OP+0])
8Ah        DELETE_GLOBAL            Clears global identifier(vars[OP+0])

90h        SETUP_LOOP               Creates a loop. OP+0 will hold the length of the loop ie: the next relatieve opcode
                                    after the loop.
92h        CONTINUE_LOOP            Continues the loop by jumping to absolute opcode OP+0.
93h        BUILD_CLASS              Creates a new class object. SP-0 holds the class name. SP-1 holds class flags. After
                                    this, there are OP+0 pairs of name (SP-3) and method objects (SP-4).
95h        COMPARE_OP               Call a comparison method. OP+0 is the comparison type. (0 = EQ, 1 = NE etc)
96h        SETUP_FINALLY            Pushes a frame onto the frame-stack. ip + OP+0 points to the FIRST fi9nally
                                    statement.
97h        SETUP_EXCEPT             Pushes a frame onto the frame-stack. ip + OP+0 points to the FIRST exception
                                    statement.
98h        END_FINALLY

81h        DELETE_NAME

82h        UNPACK_SEQUENCE

82h        FOR_ITER
5Fh        STORE_ATTR
60h        DELETE_ATTR
69h        LOAD_ATTR

A0h        BUILD_DATASTRUCTURE      Creates a datastructure with OP+0 elements. SP-0 points to the name of the
                                    datastructure, while SP-N are the element tuples. Pushes back a datastructure
                                    object.
A1h        BUILD_TUPLE              Same as BUILD_DATASTRUCTURE, except there is no name of the datastructure pushed
                                    onto the stack. Implies "list" and SP-0 points to the first element to be added.
A2h        BUILD_LIST               Same as BUILD_DATASTRUCTURE, except there is no name of the datastructure pushed
                                    onto the stack. Implies "list" and SP-0 points to the first element to be added.
A3h        BUILD_HASH               Same as BUILD_DATASTRUCTURE, except there is no name of the datastructure pushed
                                    onto the stack. Implies "hash" and SP-0 points to the first element to be added.
A4h        BUILD_SET                Same as BUILD_DATASTRUCTURE, except there is no name of the datastructure pushed
                                    onto the stack. Implies "set" and SP-0 points to the first element to be added.

85h        BUILD_SLICE
======     ====================     ==========================================



------------------------------
Opcodes with multiple operands
------------------------------

Opcodes with two or more operands are possible. They consist of having the highest bits set to 1. In effect this means
that operands starting from **C0h** to **DFh** are reserved for opcodes with 2 operands (since these opcodes have the
highest 2 bits set). Opcdoes **E0h** to **EFh** have the highest 3 bits set, so they are reserved for 3 operand opcodes.
**F0h** to **FEh** are reserved for opcodes with 4 operands. Opcode **FFh** has special meaning and is discussed in
the `Reserved opcodes`_ section.

======     ====================     ==========================================
Opcode     Value                    Description
======     ====================     ==========================================
C1h        SETUP_ELSE_LOOP          OP+0 points to the end of the while-loop, while OP+1 points to the start of the
                                    else loop.
C2h        BUILD_ATTRIB             OP+0 defines the type of the attribute (constant, property or attribute), OP+1 is
                                    the number of arguments (in case the attribute is a method)
======     ====================     ==========================================

======     ====================     ==========================================
Opcode     Value                    Description
======     ====================     ==========================================
0xE0       SETUP_EXCEPT             OP+0, OP+1 OP+2
======     ====================     ==========================================


==========      ==============================================================
Opcodes         Description
==========      ==============================================================
F0h to FEh      4 operand codes (reserved for future use)
==========      ==============================================================



----------------
Reserved opcodes
----------------
These opcodes should not be used inside Saffire bytecode. When encountered, the VM will halt execution.

======     ====================     ==========================================
Opcode     Value                    Description
======     ====================     ==========================================
FFh        <reserved>               Reserved for future use. Can be used as a marker to indicate special opcode cases.
======     ====================     ==========================================



--------------
Future opcodes
--------------
Virtual machines should be very simple in setup and this should reflect in the number of opcodes that a virtual machine
could handle. Normally, having a maximum of 256 different opcodes should be more than adequate for even the most complex
operations. Still, a virtual machine, just like a computer processor, can "evolve" overtime and accept even more "high-
end" opcodes. In order to keep the bytecode small, we will keep using only 1 byte opcodes, but have **FFh** reserved for
extensions.

Later, when 1-byte opcodes has proven not to be enough, we can use FFh as a marker that another opcode byte will follow.
For instance, the opcodes **FFh 00h** can indicate a future opcode. If even 2 bytes aren't enough, the **FFh** marker
can be used for even larger sets. **FFh FFh FFh 00h** can be distinguished as a unique opcode in a opcode-set of almost
**4 million** different opcodes. I think in this case it is safe to say: 4 million different opcodes should be enough
for everybody.





; 1 operand per opcode
STORE_ID             0x80
LOAD_CONST           0x81
LOAD_ID              0x82

JUMP_FORWARD         0x83
JUMP_IF_TRUE         0x84
JUMP_IF_FALSE        0x85
JUMP_ABSOLUTE        0x86

DUP_TOPX             0x87

LOAD_GLOBAL          0x88
STORE_GLOBAL         0x89
DELETE_GLOBAL        0x8A

SETUP_LOOP           0x90

CONTINUE_LOOP        0x92
BUILD_CLASS          0x93
BUILD_INTERFACE      0x94
COMPARE_OP           0x95
SETUP_FINALLY        0x96

JUMP_IF_FIRST_FALSE  0xA0
JUMP_IF_FIRST_TRUE   0xA1

OPERATOR             0xA8
INPLACE_OPR          0xA9

BUILD_TUPLE          0xAE
BUILD_DATASTRUCT     0xAF

STORE_ATTRIB         0xBD
LOAD_ATTRIB          0xBE
CALL                 0xBF


; 2 operands per opcode
SETUP_ELSE_LOOP      0xC1
BUILD_ATTRIB         0xC2

; 3 operands per opcode
SETUP_EXCEPT         0xE0

RESERVED             0xFF
