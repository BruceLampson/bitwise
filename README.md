# PHP Bitwise Tutorial
The bitwise operators and binary math in general have always been a mystery to me. If not for studying for the zend certification I still would probably not care to learn them :) However here I am and I finally got down the mystery of bits and bytes.

What this tutorial will cover:

1. What are bits and bytes and binary math

2. PHP's Bitwise Operators

#Bits, Bytes, and Binary Math

###BINARY MATH INTRODUCTION

The bitwise operators utilize something called Binary Math. If you already know binary math, skip ahead. Binary math is a BASE 2 numbering system, where as our normal everyday numbering system is a BASE 10 system. Think back to elementary school where we learned numbers this way...

Think of the number 4768. Thats a normal everyday decimal number.

If you write that out full its 4 THOUSAND, 7 HUNDRED, 6 TENS, 8 ONES
or (4 * 103) + (7 * 102) + (6 * 101) + (8 * 100) = 4768

The BASE 2 system has the same concept however it goes by 2's instead of 10s. So you can only have a value of 0 or 1. Lets look at a binary number
00101101 = (0 * 27) + (0 * 26) + (1 * 25) + (0 * 24) + (1 * 23) + (1 * 22) + (0 * 21) + (1 * 20) = 32 + 8 + 4 + 1 = 45

Wow that's a lot of math. Lets break it down piece by piece starting with the first parentheses.

(0 * 27) which means 0 TIMES 2 to the POWER of 7 or 0 * ( 2 * 2 * 2 * 2 * 2 * 2 * 2) which basically comes out to 0 * 128 which equals 0 (0 times anything is 0)

So going down our binary number we can see it calculates like this:

0 - (0 * 128) = 0<br>
0 - (0 * 64) = 0<br>
1 - (1 * 32) = 32<br>
0 - (0 * 16) = 0<br>
1 - (1 * 8) = 8<br>
1 - (1 * 4) = 4<br>
0 - (0 * 2) = 0<br>
1 - (1 * 1) = 1<br>

So add those all up together 32 + 8 + 4 + 1 and you get 45

What is a bit? A bit is a representation of 1 or 0. Basically OFF and ON. Why do computers use such simple math? Well computers process with electric current so if the current is over a certain level the computer considers that to mean ON or 1 and if it is under that level it is set to OFF or 0.

What is a byte? A byte is made up of 8 bits and the highest value of a byte is 255, which would mean every bit is set. We will look at why a byte's maximum value is 255 in just a second.

What does a byte look like?

<table>
    <tbody>
        <tr> 
            <td colspan="11" align="center"> 
              1 Byte ( 8 bits )
            </td>
        </tr>
    <tr>
        <td width="100">
        Place Value
        </td>
        <td> 
          128
        </td>
        <td> 
          64
        </td>
        <td> 
          32
        </td>
        <td> 
          16
        </td>
        <td> 
          8
        </td>
        <td> 
          4
        </td>
        <td> 
          2
        </td>
        <td> 
          1
        </td>
        <td></td>
        <td></td>
    </tr>
    </tbody>
</table>


That is a representation of 1 Byte. 
The "Place Value" column represents the math we did doing 2 to the power of 7,6,5,4,3,2,1,0

So if all bits are set and the value = 255 my byte would look like this

<table>
    <tbody>
        <tr> 
            <td colspan="11"> 
                1 Byte ( 8 bits )
            </td>
        </tr>
    <tr> 
        <td>
            Place Value
        </td>
        <td> 
          128
        </td>
        <td> 
          64
        </td>
        <td> 
          32
        </td>
        <td> 
          16
        </td>
        <td> 
          8
        </td>
        <td> 
          4
        </td>
        <td> 
          2
        </td>
        <td> 
          1
        </td>
        <td></td>
        <td></td>
    </tr>
    <tr> 
        <td width="100">&nbsp;</td>
        <td> 
          <div align="center">1
        </td>
        <td> 
          <div align="center">1
        </td>
        <td> 
          <div align="center">1
        </td>
        <td> 
          <div align="center">1
        </td>
        <td> 
          <div align="center">1
        </td>
        <td> 
          <div align="center">1
        </td>
        <td> 
          <div align="center">1
        </td>
        <td> 
          <div align="center">1
        </td>
        <td>
          <div align="center">=
        </td>
        <td>255</td>
    </tr>
    </tbody>
</table>

How do we get 255?

Lets take it right to left and add up all those values together
1 + 2 + 4 + 8 + 16 + 32 + 64 + 128 = 255

What would the number 22 look like?

<table>
    <tbody>
    <tr> 
    <td colspan="11"> 
    1 
    Byte ( 8 bits )
    </td>
    </tr>
    <tr> 
    <td>Place 
    Value</td>
    <td> 
    128
    </td>
    <td> 
    64
    </td>
    <td> 
    32
    </td>
    <td> 
    16
    </td>
    <td> 
    8
    </td>
    <td> 
    4
    </td>
    <td> 
    2
    </td>
    <td> 
    1
    </td>
    <td></td>
    <td></td>
    </tr>
    <tr> 
    <td>&nbsp;</td>
    <td> 
    <div align="center">0
    </td>
    <td> 
    <div align="center">0
    </td>
    <td> 
    <div align="center">0
    </td>
    <td> 
    <div align="center">1
    </td>
    <td> 
    <div align="center">0
    </td>
    <td> 
    <div align="center">1
    </td>
    <td> 
    <div align="center">1
    </td>
    <td> 
    <div align="center">0
    </td>
    <td>
    <div align="center">=
    </td>
    <td>
    <div align="center">22
    </td>
    </tr>
    </tbody>
</table>
            
2 + 4 + 16 = 22

Lets look at some other examples of decimal to binary, the ones on the end try for yourself.

43 = 00101011<br>
4 = 00000100<br>
230 = ?<br>
65 = ?<br>
31 = ?<br>

Special thanks to **Jim Plush**

#PHP'S BITWISE OPERATORS

<table>
<thead> 
<tr> 
<th>Example</th>
<th>Name</th>
<th>Result</th>
</tr>
</thead>
<tbody> 
<tr> 
<td>$a &amp; $b</td>
<td>And</td>
<td>Bits that are set in both $a and $b are set.</td>
</tr>
<tr> 
<td>$a | $b</td>
<td>Or</td>
<td>Bits that are set in either $a or $b are set.</td>
</tr>
<tr> 
<td>$a ^ $b</td>
<td>Xor</td>
<td>
Bits that are set in $a or $b but not both are set. </td>
</tr>
<tr> 
<td>~ $a</td>
<td>Not</td>
<td>
Bits that are set in $a are not set, and vice versa. </td>
</tr>
<tr> 
<td>$a &lt;&lt; $b</td>
<td>Shift left</td>
<td>
Shift the bits of $a $b steps to the left (each step means "multiply by 
two") </td>
</tr>
<tr> 
<td>$a &gt;&gt; $b</td>
<td>Shift right</td>
<td>
Shift the bits of $a $b steps to the right (each step means "divide by 
two") </td>
</tr>
</tbody> 
</table>


####Lets use two variables to get started with the "And" operator &. 
The & or "And" operator takes two values and returns a decimal version of the binary values the left and right variable share. So using our tables above we can see that the only bit these two share is in the 8 position so $a & $b = 8.

```php
$a =	9;
$b =	10;
echo $a & $b;
```


