# Content

## basics

clear transcript window.

```
Transcript clear.
```

w1-redo4 - save your code with iceberg

### w1-redo4

left click > Browse > Iceberg > Add > (project name) > OK > double clik > add package > select > commit

w2-s1 - messages
w2-s2 - messages for java programmers
w2-s3 - messages composition
w2-s4 - expression sequence
w2-s6 - blocks

```
[:x :y | x+y] value: 5 value: 7

```

w2-s7 - loops

ex 1

```
1 to: 100 do:
	[ :i | Transcript show: i; space ]
```

ex 2

```
#(15 10 19 65) do:
	[ :i | Transcript show: i; cr ]

```

ex 3 - while loop with multiple statements

```
|n x|
Transcript clear.
n := 1.
x := 5.

[ n < 1000 ] whileTrue: [ n := n*2. x:= x+2.].
Transcript show: n .
Transcript space .
Transcript show: x .
```

w2-s8 - booleans
w2-s9 - paranthesis vs square brackets
w2-s10 - youself
w2-s11 - essence of dispatch
