# 6lang/Perl 6 Golfing Cheatsheet

As I'm getting bored with code golf, I decided to share some of the
tricks with the world. If that document makes golfing less fun for
you, you can close your eyes while reading it.

**Please note:** This document is mostly focused on golf platforms that
count codepoints instead of UTF-8 bytes. That said, I will try to
include unicode-unrelated tricks too.

**Also:** This document does not list *everything* and probably it
  never will. Contributions are welcome.

## Numbers

### Unicode
If one of the numbers that you are using is one of these:
```
NaN -0.5 0.00625 0.025 0.0375 0.05 0.0625 0.083333 0.1 0.111111 0.125
0.142857 0.15 0.166667 0.1875 0.2 0.25 0.333333 0.375 0.4 0.416667 0.5
0.583333 0.6 0.625 0.666667 0.75 0.8 0.833333 0.875 0.916667 1 1.5 2
2.5 3 3.5 4 4.5 5 5.5 6 6.5 7 7.5 8 8.5 9 10 11 12 13 14 15 16 17 18
19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41
42 43 44 45 46 47 48 49 50 60 70 80 90 100 200 300 400 500 600 700 800
900 1000 2000 3000 4000 5000 6000 7000 8000 9000 10000 20000 30000
40000 50000 60000 70000 80000 90000 100000 200000 216000 300000 400000
432000 500000 600000 700000 800000 900000 1000000 100000000
10000000000 1000000000000

# perl6 -e 'for ^0x10FFFF { .unival.say }' | sort -un
```

Then use the corresponding unicode character.
```perl6
say ㊿
#   50

say 兆
#   1000000000000
```


### Whitespace between numbers and ops
```perl6
say 2 xx 3
```
```perl6
say ②xx③
```


### Topic variable increment
```perl6
say $_++
```
```perl6
say .++
```


## Strings

Use uninames, error messages and other built-in strings instead of
string literals:
```perl6
say (‘♔’…‘♙’)».uniname».words»[2]
#   KING QUEEN ROOK BISHOP KNIGHT PAWN
```


## Lists

```perl6
my ($a, $b, $c) = 42, 52, 62;
my$z=«25$a$b$c»
#    (25,$a,$b,$c)
```


## Loops

This one is a bit tough to get into your code, but it does help
sometimes:

```perl6
 say(42)for ^10
#say(42)xx⑤
```


## Conditionals

Use junctions if possible

```perl6
say 42 if 0||1
```
```perl6
say 42 if 0|1
```

Note that you can use junctions as sub args, and you get a junction
back.


## 1-character if-then

```perl6
42==42&&say ‘hello’;
42==42>say ‘hello’;
42==42≠say ‘hello’;
```


# Other

## Base 0x10FFFF

This techique is explained in more detail in [this post](https://perl6advent.wordpress.com/2017/12/23/day-23-the-wonders-of-perl6-golf/).

## infix .
```perl6
say (^50).max;
say ^50 .max;
```
