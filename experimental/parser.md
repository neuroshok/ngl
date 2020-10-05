a+b

        add
       /   \
     a       b
     
001 L
010 Plus 
100 Add seq<L, Plus, L>

a 001 101
+ 010 110
b 001 101

_________________________________________________
a+b*c+(a*b)
    add
   /   \
  a    add
      /   \
     b     c
00001 D 
00010 Plus
00100 Bxpr
10000 Self

a 00101
+ 00110
b 10101
+ 00110
c 10101
+ 00110
d 00101

rec = or<Self L>
Bxpr = seq<rec OP rec>

_________________________________________________
(a+b)*c
xpr = L | (Bxpr)
Bxpr = xpr op xpr

_________________________________________________
ncna
nc = seq<n c>
xpr = seq<nc not<nc>>

0010 nc
0100 not
1000 xpr

n 0000
c 0010
n 0000
a 1100