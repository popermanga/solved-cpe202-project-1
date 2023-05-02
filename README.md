Download Link: https://assignmentchef.com/product/solved-cpe202-project-1
<br>
Goal: Write a Python program to generate all the permutations of the characters in a string.  This will give you a chance to review some simple Python constructs, i.e. Strings and Lists and solidify your understanding of recursion.

Your program <strong><u>must</u></strong> meet the following specification.  You are to write a Python function <strong>perm_gen_lex </strong>that:

<ul>

 <li>Takes a string as a single input argument. <u>You may assume the input string consists 0 or more unique</u> <u>lower-case letters in alphabetical order.</u></li>

 <li>Returns a Python <strong><u>list</u></strong> of strings where each string represents a permutation of the input string. The list of permutations must be in lexicographic order (dictionary order). Note: If you follow the pseudo code below, your list will be constructed such that this condition will be met. <strong>Do not sort the list.</strong></li>

 <li>Is well structured, commented, and easy to read. Contains a docstring explaining its purpose.</li>

 <li>Is recursive and follows the pseudo code below.</li>

</ul>




<table width="0">

 <tbody>

  <tr>

   <td width="122"><strong>Argument:</strong></td>

   <td width="423">‘’</td>

  </tr>

  <tr>

   <td width="122"><strong>Returns: </strong> </td>

   <td width="423">[]</td>

  </tr>

  <tr>

   <td width="122"><strong>Argument:</strong></td>

   <td width="423">‘a’</td>

  </tr>

  <tr>

   <td width="122"><strong>Returns: </strong> </td>

   <td width="423">[‘a’]</td>

  </tr>

  <tr>

   <td width="122"><strong>Argument:</strong></td>

   <td width="423">‘abc’</td>

  </tr>

  <tr>

   <td width="122"><strong>Returns: </strong></td>

   <td width="423">[‘abc’, ‘acb’, ‘bac’, ‘bca’, ‘cab’, ‘cba’]</td>

  </tr>

 </tbody>

</table>




Pseudo code for a recursive algorithm to generate permutations in lexicographic order.

<strong>You must follow this pseudo code. </strong>




For each character in the input string:

Form a simpler string by removing the character from the input string

Generate all permutations of the simpler string recursively (i.e. call the perm_gen_lex function with the simpler string)

Add the removed character to the front of each permutation of the simpler string, and add the resulting permutation to the list




<strong> </strong>

Note:  For a string with n characters, you program will return a list contain n! strings.  Note that n! grows very quickly.  For example, 15! is roughly 1.3*10<sup>12</sup> .  Thus it is probably not a good idea to test your program with long strings if you plan on turning the assignment in ‘on’ time.




<strong> </strong>




<strong> </strong>

<strong>Part2: Base conversion </strong>

One algorithm for converting a base 10 number to base b involves repeated division by the base b. Initially one divides the number by b. The remainder from this division is the units digit (the rightmost digit) in the base b representation of the number (it is the part of the number that contains no powers of b). The quotient is then divided by b on the next iteration. The remainder from this division gives the next base b digit from the right. The quotient from this division is used in the next iteration. The algorithm stops when the quotient is 0. Note that at each iteration the remainder from the division is the next base b digit from the right—that is, this algorithm finds the digits for the base b number in reverse order. Here is an example for converting 30 to base 4:

quotient remainder         ——– ———

30/4       7        2

7/4        1        3

1/4        0        1

The answer is read bottom to top in the remainder column, so 30 (base 10) = 132 (base 4).

Think about how this is recursive in nature:

If you want to convert x (30 in our example) to base b (4 in our example), the rightmost digit is the remainder x % b. To get the rest of the digits, you perform the same process on what is left; that is, you convert the quotient x // b to base b. If x // b is 0, there is no rest; x is a single base b digit and that digit is x % b (which also is just x).




In a file named <strong>base_convert.py</strong>, write a recursive function named convert() that will take a non-negative integer num (base 10) and a base b (integer from 2 to 16) and return a string representing the base b number:

def convert(num, b):

“””Recursive function that returns a string representing num in the base b”””

convert(30,4) returns “132” convert(45,2)) returns “101101” convert(316,16) returns “13C”




Note that for bases &gt; 10, the symbols used for 10, 11, 12, 13, 14, 15 are A, B, C, D, E, F respectively.




<strong> </strong>

<strong> </strong>

<strong>Part3: A Teddy Bear Picnic </strong>

This question involves a game with teddy bears. The game starts when I give you some bears. You can then repeatedly give back some bears, but you must follow these rules (where n is the number of bears that you currently have):

<ol>

 <li>If n is even, then you may give back n/2 bears.</li>

 <li>If n is divisible by 3 or 4, then you may multiply the last two digits of n and give back this many bears.</li>

 <li>If n is divisible by 5, then you may give back 42 bears.</li>

</ol>

The goal of the game is to end up with EXACTLY 42 bears.

For example, suppose that you start with 250 bears. Then you could make these moves:

<ul>

 <li>Start with 250 bears.</li>

 <li>Since 250 is divisible by 5, you may return 42 of the bears, leaving you with 208 bears.</li>

 <li>Since 208 is even, you may return half of the bears, leaving you with 104 bears.</li>

 <li>Since 104 is even, you may return half of the bears, leaving you with 52 bears.</li>

 <li>Since 52 is divisible by 4, you may multiply the last two digits (resulting in 10) and return these 10 bears. This leaves you with 42 bears.</li>

</ul>

You have reached the goal!

Write a recursive function to meet this specification:

def bears(n):

“””A True return value means that it is possible to win     the bear game by starting with n bears. A False return value means     that it is not possible to win the bear game by starting with n     bears.”””




Examples:

<ul>

 <li>bears(250) is True (as shown above)</li>

 <li>bears(42) is True</li>

 <li>bears(53) is False</li>

 <li>bears(41) is False</li>

</ul>




Although this problem may seem silly at first, it’s an example of a reachability problem, which is a problem that arises in many areas of computer science.<u><a href="https://en.wikipedia.org/wiki/Reachability_problem">https://en.wikipedia.org/wiki/Reachability_problem</a></u>