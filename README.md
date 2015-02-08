# PHP Bitwise Tutorial by Jim Plush
The bitwise operators and binary math in general have always been a mystery to me. If not for studying for the zend certification I still would probably not care to learn them :) However here I am and I finally got down the mystery of bits and bytes.

What this tutorial will cover:

1. What are bits and bytes and binary math

2. PHP's Bitwise Operators

3. A simple usecase for why you would want to use bitwise operators

PART 1 Bits, Bytes, and Binary Math

###BINARY MATH INTRODUCTION

The bitwise operators utilize something called Binary Math. If you already know binary math, skip ahead. Binary math is a BASE 2 numbering system, where as our normal everyday numbering system is a BASE 10 system. Think back to elementary school where we learned numbers this way...

Think of the number 4768. Thats a normal everyday decimal number.

If you write that out full its 4 THOUSAND, 7 HUNDRED, 6 TENS, 8 ONES
or (4 * 103) + (7 * 102) + (6 * 101) + (8 * 100) = 4768

The BASE 2 system has the same concept however it goes by 2's instead of 10s. So you can only have a value of 0 or 1. Lets look at a binary number
00101101 = (0 * 27) + (0 * 26) + (1 * 25) + (0 * 24) + (1 * 23) + (1 * 22) + (0 * 21) + (1 * 20) = 32 + 8 + 4 + 1 = 45

Wow thats alot of math. Lets break it down piece by piece starting with the first parentheses.

(0 * 27) which means 0 TIMES 2 to the POWER of 7 or 0 * ( 2 * 2 * 2 * 2 * 2 * 2 * 2) which basically comes out to 0 * 128 which equals 0 (0 times anything is 0)

so going down our binary number we can see it calculates like this:

0 - (0 * 128) = 0
0 - (0 * 64) = 0
1 - (1 * 32) = 32
0 - (0 * 16) = 0
1 - (1 * 8) = 8
1 - (1 * 4) = 4
0 - (0 * 2) = 0
1 - (1 * 1) = 1

so add those all up together 32 + 8 + 4 + 1 and you get 45
