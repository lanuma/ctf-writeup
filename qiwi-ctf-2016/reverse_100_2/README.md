##Reverse_100_2
========

> Angga Lanuma | 19 November 2016
--------------------------------------

> I have a [snake](./task.pyc). CrackMe!

I download the file and given task.pyc. The file is a compiled python file

So, i try to uncompile task.pyc using [uncompyle2](https://github.com/wibiti/uncompyle2)
and after clean the code we get:

```
import marshal
src = 'YwAAAAADAAAAGAAAAEMAAABz7wAAAGQBAGoAAGcAAGQCAGQDAGQEAGQFAGQGAGQHAGQIAGQJAGQKAGQLAGQMAGQNAGQOAGQPAGQMAGcPAERdHAB9AAB0AQB0AgB8AACDAQBkEAAXgwEAXgIAcToAgwEAfQEAdAMAZBEAgwEAfQIAfAIAfAEAawIAcuYAZAEAagAAZwAAZBIAZBMAZBQAZBUAZBYAZBcAZBgAZBkAZBoAZBsAZBwAZB0AZB4AZAsAZBwAZB8AZAMAZB0AZAgAZB4AZCAAZCEAZxYARF0VAH0AAHwAAGoEAGQiAIMBAF4CAHHGAIMBAEdIbgUAZCMAR0hkAABTKCQAAABOdAAAAAB0AQAAAF50AQAAADR0AQAAAEt0AQAAAGl0AQAAAC50AQAAAC90AQAAAE50AQAAAGp0AQAAAFB0AQAAAG90AQAAAD90AQAAAGx0AQAAADJ0AQAAAFRpAwAAAHMJAAAAWW91IHBhc3M6dAEAAABzdAEAAAB5dAEAAABudAEAAAB0dAEAAAA6dAEAAAB7dAEAAAB3dAEAAABxdAEAAABFdAEAAAA2dAEAAABmdAEAAABYdAEAAAB1dAEAAABhdAEAAAAxdAEAAAB9dAUAAABST1QxM3MFAAAATm8gOigoBQAAAHQEAAAAam9pbnQDAAAAY2hydAMAAABvcmR0CQAAAHJhd19pbnB1dHQGAAAAZGVjb2RlKAMAAAB0AQAAAGV0AwAAAHRtcHQGAAAAcGFzc3dkKAAAAAAoAAAAAHMHAAAAdGFzay5weVIcAAAAAgAAAHMKAAAAAAFfAQwBDAFvAQ=='.decode('base64')
code = marshal.loads(src)
exec code

```

change syntax **exec** to **print**
```
import marshal
src = 'YwAAAAADAAAAGAAAAEMAAABz7wAAAGQBAGoAAGcAAGQCAGQDAGQEAGQFAGQGAGQHAGQIAGQJAGQKAGQLAGQMAGQNAGQOAGQPAGQMAGcPAERdHAB9AAB0AQB0AgB8AACDAQBkEAAXgwEAXgIAcToAgwEAfQEAdAMAZBEAgwEAfQIAfAIAfAEAawIAcuYAZAEAagAAZwAAZBIAZBMAZBQAZBUAZBYAZBcAZBgAZBkAZBoAZBsAZBwAZB0AZB4AZAsAZBwAZB8AZAMAZB0AZAgAZB4AZCAAZCEAZxYARF0VAH0AAHwAAGoEAGQiAIMBAF4CAHHGAIMBAEdIbgUAZCMAR0hkAABTKCQAAABOdAAAAAB0AQAAAF50AQAAADR0AQAAAEt0AQAAAGl0AQAAAC50AQAAAC90AQAAAE50AQAAAGp0AQAAAFB0AQAAAG90AQAAAD90AQAAAGx0AQAAADJ0AQAAAFRpAwAAAHMJAAAAWW91IHBhc3M6dAEAAABzdAEAAAB5dAEAAABudAEAAAB0dAEAAAA6dAEAAAB7dAEAAAB3dAEAAABxdAEAAABFdAEAAAA2dAEAAABmdAEAAABYdAEAAAB1dAEAAABhdAEAAAAxdAEAAAB9dAUAAABST1QxM3MFAAAATm8gOigoBQAAAHQEAAAAam9pbnQDAAAAY2hydAMAAABvcmR0CQAAAHJhd19pbnB1dHQGAAAAZGVjb2RlKAMAAAB0AQAAAGV0AwAAAHRtcHQGAAAAcGFzc3dkKAAAAAAoAAAAAHMHAAAAdGFzay5weVIcAAAAAgAAAHMKAAAAAAFfAQwBDAFvAQ=='.decode('base64')
code = marshal.loads(src)
print code

```

After modifying the code save to the new file, example [task_uncompyle.py](task_uncompyle.py)

After that, i write python script to disassemley **task_uncompyle.py** to read what the code do.

```
#!/usr/bin/python

import task_uncompyle
import dis

print dis.dis(task_uncompyle)

```

we get output:
`
Disassembly of code:
  3           0 LOAD_CONST               1 ('')
              3 LOAD_ATTR                0 (join)
              6 BUILD_LIST               0
              9 LOAD_CONST               2 ('^')
             12 LOAD_CONST               3 ('4')
             15 LOAD_CONST               4 ('K')
             18 LOAD_CONST               5 ('i')
             21 LOAD_CONST               6 ('.')
             24 LOAD_CONST               7 ('/')
             27 LOAD_CONST               8 ('N')
             30 LOAD_CONST               9 ('j')
             33 LOAD_CONST              10 ('P')
             36 LOAD_CONST              11 ('o')
             39 LOAD_CONST              12 ('?')
             42 LOAD_CONST              13 ('l')
             45 LOAD_CONST              14 ('2')
             48 LOAD_CONST              15 ('T')
             51 LOAD_CONST              12 ('?')
             54 BUILD_LIST              15
             57 GET_ITER            
        >>   58 FOR_ITER                28 (to 89)
             61 STORE_FAST               0 (e)
             64 LOAD_GLOBAL              1 (chr)
             67 LOAD_GLOBAL              2 (ord)
             70 LOAD_FAST                0 (e)
             73 CALL_FUNCTION            1
             76 LOAD_CONST              16 (3)
             79 BINARY_ADD          
             80 CALL_FUNCTION            1
             83 LIST_APPEND              2
             86 JUMP_ABSOLUTE           58
        >>   89 CALL_FUNCTION            1
             92 STORE_FAST               1 (tmp)

  4          95 LOAD_GLOBAL              3 (raw_input)
             98 LOAD_CONST              17 ('You pass:')
            101 CALL_FUNCTION            1
            104 STORE_FAST               2 (passwd)

  5         107 LOAD_FAST                2 (passwd)
            110 LOAD_FAST                1 (tmp)
            113 COMPARE_OP               2 (==)
            116 POP_JUMP_IF_FALSE      230

  6         119 LOAD_CONST               1 ('')
            122 LOAD_ATTR                0 (join)
            125 BUILD_LIST               0
            128 LOAD_CONST              18 ('s')
            131 LOAD_CONST              19 ('y')
            134 LOAD_CONST              20 ('n')
            137 LOAD_CONST              21 ('t')
            140 LOAD_CONST              22 (':')
            143 LOAD_CONST              23 ('{')
            146 LOAD_CONST              24 ('w')
            149 LOAD_CONST              25 ('q')
            152 LOAD_CONST              26 ('E')
            155 LOAD_CONST              27 ('6')
            158 LOAD_CONST              28 ('f')
            161 LOAD_CONST              29 ('X')
            164 LOAD_CONST              30 ('u')
            167 LOAD_CONST              11 ('o')
            170 LOAD_CONST              28 ('f')
            173 LOAD_CONST              31 ('a')
            176 LOAD_CONST               3 ('4')
            179 LOAD_CONST              29 ('X')
            182 LOAD_CONST               8 ('N')
            185 LOAD_CONST              30 ('u')
            188 LOAD_CONST              32 ('1')
            191 LOAD_CONST              33 ('}')
            194 BUILD_LIST              22
            197 GET_ITER            
        >>  198 FOR_ITER                21 (to 222)
            201 STORE_FAST               0 (e)
            204 LOAD_FAST                0 (e)
            207 LOAD_ATTR                4 (decode)
            210 LOAD_CONST              34 ('ROT13')
            213 CALL_FUNCTION            1
            216 LIST_APPEND              2
            219 JUMP_ABSOLUTE          198
        >>  222 CALL_FUNCTION            1
            225 PRINT_ITEM          
            226 PRINT_NEWLINE       
            227 JUMP_FORWARD             5 (to 235)

  7     >>  230 LOAD_CONST              35 ('No :(')
            233 PRINT_ITEM          
            234 PRINT_NEWLINE       
        >>  235 LOAD_CONST               0 (None)
            238 RETURN_VALUE        


`

there are something interesting at line 49 to 70:
`synt:{wqE6fXuofa4XNu1}`

and the clue in line 77 that give me information ROT13 ecnryption

So, i decode using ROT13 in python-cli

``` >>> "synt:{wqE6fXuofa4XNu1}".decode("rot13") ```

Finally i found the flag is: ***flag:{jdR6sKhbsn4KAh1}***