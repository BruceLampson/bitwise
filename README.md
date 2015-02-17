# PHP Bitwise Tutorial
The bitwise operators and binary math in general have always been a mystery to me. If not for studying for the <a href="http://www.zend.com/en/yellow-pages/ZEND024326" target="_blank">Zend PHP Certified Engineer</a> exam. I still would probably not care to learn them :) However here I am and I finally got down the mystery of bits and bytes.

What this tutorial will cover:

1. What are bits and bytes and binary math

2. PHP's Bitwise Operators

#Bits, Bytes, Binary and Hex Math

###BINARY MATH INTRODUCTION

The bitwise operators utilize something called Binary Math. If you already know binary math, skip ahead. Binary math is a BASE 2 numbering system, where as our normal everyday numbering system is a BASE 10 system. Think back to elementary school where we learned numbers this way...

Think of the number 4768. That's a normal everyday decimal number.

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
        <td>&nbsp;</td>
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

###Converting from HEX to DEC

HEX numbers are composed of digits 0 through 9 like DEC but also adds A-F

<table>
<tbody><tr align="center">
<td>HEX</td>
<td>0</td>
<td>1</td>
<td>2</td>
<td>3</td>
<td>4</td>
<td>5</td>
<td>6</td>
<td>7</td>
<td>8</td>
<td>9</td>
<td>A</td>
<td>B</td>
<td>C</td>
<td>D</td>
<td>E</td>
<td>F</td>
</tr>
<tr align="center">
<td>DEC</td>
<td>0</td>
<td>1</td>
<td>2</td>
<td>3</td>
<td>4</td>
<td>5</td>
<td>6</td>
<td>7</td>
<td>8</td>
<td>9</td>
<td>10</td>
<td>11</td>
<td>12</td>
<td>13</td>
<td>14</td>
<td>15</td>
</tr>
</tbody>
</table>


###Here is a HEX number: 1E5DF


To convert this to a DEC, we need to define the base for our power function. Since HEX is based on 16 different digits [0-9A-F], our base is 16.<br>

To convert from HEX to DEC, follow these steps: <br>

We know that F = 15 in DEC so we use this formula	(15 * 16<sup>0</sup>) = 15<br>
We know that D = 13 in DEC so we use this formula	(13 * 16<sup>1</sup>) = 208<br>
We know that 5 = 5 in DEC so we use this formula	(5 * 16<sup>2</sup>) = 1280<br>
We know that E = 14 in DEC so we use this formula	(14 * 16<sup>3</sup>) = 57344<br>
We know that 1 = 1 in DEC so we use this formula	(1 * 16<sup>4</sup>) = 65536<br>
Now we add all of the numbers together to get the DEC number for HEX number 1E5DF:<br>
15 + 208 + 1280 + 57344 + 65536 = 124383<br>


So our answer is HEX 1E5DF = DEC 124383<br>


#PHP'S BITWISE OPERATORS


You can find complete detail on the PHP bitwise operators here: <a href='http://www.php.net/manual/en/language.operators.bitwise.php' target='_blank'>PHP'S BITWISE OPERATORS</a>

What are going to cover? 
We're going to cover the bitwise operators below and see how they work

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

This would output the number 8. Why?? Well lets see using our table example

<table align="left">
<tbody><tr> 
<td colspan="11"> 
  <div align="center">1 
    Byte ( 8 bits )
</td>
</tr>
<tr> 
<td>Place 
  Value</td>
<td> 
  <div align="center">128
</td>
<td> 
  <div align="center">64
</td>
<td> 
  <div align="center">32
</td>
<td> 
  <div align="center">16
</td>
<td> 
  <div align="center">8
</td>
<td> 
  <div align="center">4
</td>
<td> 
  <div align="center">2
</td>
<td> 
  <div align="center">1
</td>
<td></td>
<td></td>
</tr>
<tr> 
<td>$a</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">=</div>
</td>
<td> 
  <div align="center">9</div>
</td>
</tr>
<tr> 
<td>$b</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">=</div>
</td>
<td> 
  <div align="center">10</div>
</td>
</tr>
</tbody></table>
            
So you can see from the table the only bit they share together is the 8 bit. So 8 gets returned.. not too hard eh? Lets look at another example of the & operator.

```php
$a =	36;
$b =	103;
echo $a & $b;
```

This would output the number 36. Why?? Well lets see using our table example again

<table align="left">
<tbody><tr> 
<td colspan="11"> 
  <div align="center">1 
    Byte ( 8 bits )
</td>
</tr>
<tr> 
<td>Place 
  Value</td>
<td> 
  <div align="center">128
</td>
<td> 
  <div align="center">64
</td>
<td> 
  <div align="center">32
</td>
<td> 
  <div align="center">16
</td>
<td> 
  <div align="center">8
</td>
<td> 
  <div align="center">4
</td>
<td> 
  <div align="center">2
</td>
<td> 
  <div align="center">1
</td>
<td></td>
<td></td>
</tr>
<tr> 
<td>$a</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">=</div>
</td>
<td> 
  <div align="center">36</div>
</td>
</tr>
<tr> 
<td>$b</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">=</div>
</td>
<td> 
  <div align="center">103</div>
</td>
</tr>
</tbody></table>
            
So you can see the only bits these two share together are the bits 32 and 4 which when added together return 36. This operator is saying "I want to know what bits you both have set in the same column"

####Lets move on to the | also known as the "OR" operator.

```php
$a =	9;
$b =	10;
echo $a | $b;
```

This would output the number 11. Why?? Well lets see using our table example

<table align="left">
<tbody><tr> 
<td colspan="11"> 
  <div align="center">1 
    Byte ( 8 bits )
</td>
</tr>
<tr> 
<td>Place 
  Value</td>
<td> 
  <div align="center">128
</td>
<td> 
  <div align="center">64
</td>
<td> 
  <div align="center">32
</td>
<td> 
  <div align="center">16
</td>
<td> 
  <div align="center">8
</td>
<td> 
  <div align="center">4
</td>
<td> 
  <div align="center">2
</td>
<td> 
  <div align="center">1
</td>
<td></td>
<td></td>
</tr>
<tr> 
<td>$a</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">=</div>
</td>
<td> 
  <div align="center">9</div>
</td>
</tr>
<tr> 
<td>$b</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">=</div>
</td>
<td> 
  <div align="center">10</div>
</td>
</tr>
</tbody></table>

If you notice we have 3 bits set, in the 8, 2, and 1 column.. add those up 8+2+1 and you get 11. It is just saying "I want to know what bits either one of you guys have set".

####Moving on to the ^ operator also known as the "Xor" operator.

```php
$a =	9;
$b =	10;
echo $a ^ $b;
```

This would output the number 3. Why?? Well lets see using our table example

<table align="left">
<tbody><tr> 
<td colspan="11"> 
<div align="center">1 
Byte ( 8 bits )
</td>
</tr>
<tr> 
<td>Place 
Value</td>
<td> 
<div align="center">128
</td>
<td> 
<div align="center">64
</td>
<td> 
<div align="center">32
</td>
<td> 
<div align="center">16
</td>
<td> 
<div align="center">8
</td>
<td> 
<div align="center">4
</td>
<td> 
<div align="center">2
</td>
<td> 
<div align="center">1
</td>
<td></td>
<td></td>
</tr>
<tr> 
<td>$a</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">1</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">1</div>
</td>
<td> 
<div align="center">=</div>
</td>
<td> 
<div align="center">9</div>
</td>
</tr>
<tr> 
<td>$b</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">1</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">1</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">=</div>
</td>
<td> 
<div align="center">10</div>
</td>
</tr>
</tbody></table>

The XOR operator wants to know "Tell me what bits you both have set but I don't want any bits you share" Notice we have 3 bits set but both $a and $b share the 8 bit, we dont want that one, we just want the 2 bit and the 1 bit that they each have set but don't share. Soooo 2+1 = 3

####OK, here is one that gets tricky the ~ operator also known as the "NOT" operator.

```php
$a =	9;
$b =	10;
echo $a & ~$b;
```

This would output the number 1. Why?? Well lets see using our table example

<table align="left">
<tbody><tr> 
<td colspan="11"> 
<div align="center">1 
Byte ( 8 bits )
</td>
</tr>
<tr> 
<td>Place 
Value</td>
<td> 
<div align="center">128
</td>
<td> 
<div align="center">64
</td>
<td> 
<div align="center">32
</td>
<td> 
<div align="center">16
</td>
<td> 
<div align="center">8
</td>
<td> 
<div align="center">4
</td>
<td> 
<div align="center">2
</td>
<td> 
<div align="center">1
</td>
<td></td>
<td></td>
</tr>
<tr> 
<td>$a</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">1</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">1</div>
</td>
<td> 
<div align="center">=</div>
</td>
<td> 
<div align="center">9</div>
</td>
</tr>
<tr> 
<td>$b</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">1</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">1</div>
</td>
<td> 
<div align="center">0</div>
</td>
<td> 
<div align="center">=</div>
</td>
<td> 
<div align="center">10</div>
</td>
</tr>
</tbody></table>


The NOT operator wants to know what is set in $a but NOT set in $b because we marked $b with the ~operator in front of it. So looking at our table we can see the only bit set in $a thats not in $b is 1.

What happens if we do this...

```php
$a =	9;
$b =	10;
echo ~$a & $b;
```

We get the value 2, because we want the bits set in $b but NOT set in $a this time, so since they both share the 8 bit, 2 bit is the only one $b has that $a does not.


####BIT SHIFTING TIME!!! 

```php
$a =	16;
echo $a << 2;
```

This would output the number 64. Why?? Well lets see using our table example

<table align="left">
<tbody><tr> 
<td colspan="11"> 
  <div align="center">1 
    Byte ( 8 bits )
</td>
</tr>
<tr> 
<td>Place 
  Value</td>
<td> 
  <div align="center">128
</td>
<td> 
  <div align="center">64
</td>
<td> 
  <div align="center">32
</td>
<td> 
  <div align="center">16
</td>
<td> 
  <div align="center">8
</td>
<td> 
  <div align="center">4
</td>
<td> 
  <div align="center">2
</td>
<td> 
  <div align="center">1
</td>
<td></td>
<td></td>
</tr>
<tr> 
<td>$a - BEFORE!</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">=</div>
</td>
<td> 
  <div align="center">16</div>
</td>
</tr>
<tr> 
<td>$a - AFTER!</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">1</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">0</div>
</td>
<td> 
  <div align="center">=</div>
</td>
<td> 
  <div align="center">64</div>
</td>
</tr>
</tbody></table>

How do we get 64? well bit shifting tells PHP to take the variable $a which in our case is 16 and shift if 2 bits which is basically like saying take 16 and multiply it by 2 twice. So 16 X 2 = 32 x 2 = 64

Special thanks to **Jim Plush**
