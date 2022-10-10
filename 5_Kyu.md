# Python Coding Challenges (5 Kyu) <img align="right" src="https://media.tenor.com/4_5IAe-TSAQAAAAi/capoo-bugcat.gif" height="100"/>
<br>

## Find the unique string

**DESCRIPTION:**

There is an array of strings. All strings contains similar letters except one. Try to find it!

```python
find_uniq([ 'Aa', 'aaa', 'aaaaa', 'BbBb', 'Aaaa', 'AaAaAa', 'a' ]) # => 'BbBb'
find_uniq([ 'abc', 'acb', 'bac', 'foo', 'bca', 'cab', 'cba' ]) # => 'foo'
```
Strings may contain spaces. Spaces are not significant, only non-spaces symbols matters. E.g. string that contains only spaces is like empty string.

It’s guaranteed that array contains more than 2 strings.<br>
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def find_uniq(arr):
>    sett = set(arr[0].lower())
>    l = [1 if (set(i.lower())==sett) else 0  for i in arr ]
>    return arr[l.index(1)] if l.count(1)==1 else arr[l.index(0)]
>```
</details>

---
<br>

## Moving Zeros To The End

**DESCRIPTION:**

Write an algorithm that takes an array and moves all of the zeros to the end, preserving the order of the other elements.

```python
move_zeros([1, 0, 1, 2, 0, 1, 3]) # returns [1, 1, 2, 1, 3, 0, 0]
```
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def move_zeros(lst):
>    i=0
>    while(i<len(lst)):
>        if(lst[i]==0):
>            lst.remove(0)
>            lst.append(0)
>        i+=1         
>    return lst
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>  def move_zeros(array):
>    return [x for x in array if x] + [0]*array.count(0)
>```

></details>

---
<br>

## Simple Pig Latin

**DESCRIPTION:**

Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.

**Examples**
  
```python
pig_it('Pig latin is cool') # igPay atinlay siay oolcay
pig_it('Hello world !')     # elloHay orldway !
```
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def pig_it(text):
>    #your code here
>    return ' '.join([(i[1:]+i[0]+'ay') if i not in ',.!;:?' else i for i in text.split()])
>```
</details>

---
<br>
  
  ## Valid Parentheses

**DESCRIPTION:**

Write a function that takes a string of parentheses, and determines if the order of the parentheses is valid. The function should return ```true``` if the string is valid, and ```false``` if it's invalid.

**Examples**
  
```python
"()"              =>  true
")(()))"          =>  false
"("               =>  false
"(())((()())())"  =>  true
```
  
**Constraints**
  
 ```0 <= input.length <= 100 ```
  
 Along with opening (```(```) and closing (```)```) parenthesis, input may contain any valid ASCII characters. Furthermore, the input string may be empty and/or **not** contain any parentheses at all. Do not treat other forms of brackets as parentheses (e.g. ```[]```, ```{}```, ```<>```). 
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def valid_parentheses(string):
>    #your code here
>    l = []
>    list_new = ''.join([i for i in string if i in '()'])
>    while len(list_new) >2:
>        list_new = ''.join(list_new.split('()'))
>        if list_new == l : break
>        l = list_new
>    return ''.join(list_new.split('()')) == '' 
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def valid_parentheses(string):
>    cnt = 0
>    for char in string:
>        if char == '(': cnt += 1
>        if char == ')': cnt -= 1
>        if cnt < 0: return False
>    return True if cnt == 0 else False
>```

></details>

---
<br>

  ## Human Readable Time

**DESCRIPTION:**

  Write a function, which takes a non-negative integer (seconds) as input and returns the time in a human-readable format (```HH:MM:SS```)

  * ```HH``` = hours, padded to 2 digits, range: 00 - 99
  * ```MM``` = minutes, padded to 2 digits, range: 00 - 59
  * ```SS``` = seconds, padded to 2 digits, range: 00 - 59
  
  The maximum time never exceeds 359999 ```(99:59:59)```
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def make_readable(seconds):
>    # Do something
>    h = '0' + str(seconds // 3600) if len(str(seconds // 3600)) <2 else seconds // 3600
>    m = '0' + str((seconds%3600)//60) if len(str((seconds%3600)//60)) <2 else (seconds%3600)//60
>    s = '0' + str((seconds%3600)%60) if len(str((seconds%3600)%60)) <2 else (seconds%3600)%60
>    return '{}:{}:{}'.format(h, m,s)
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def make_readable(n):
>    return f'{n//3600:02d}:{(n%3600)//60:02d}:{n%60:02d}'
>```

></details>

---
<br>

  ## Where my anagrams at?

**DESCRIPTION:**

What is an anagram? Well, two words are anagrams of each other if they both contain the same letters. For example:

**Examples**
  
```python
'abba' & 'baab' == true

'abba' & 'bbaa' == true

'abba' & 'abbba' == false

'abba' & 'abca' == false
```
  
Write a function that will find all the anagrams of a word from a list. You will be given two inputs a word and an array with words. You should return an array of all the anagrams or an empty array if there are none. For example:
  
```python
anagrams('abba', ['aabb', 'abcd', 'bbaa', 'dada']) => ['aabb', 'bbaa']

anagrams('racer', ['crazer', 'carer', 'racar', 'caers', 'racer']) => ['carer', 'racer']

anagrams('laser', ['lazing', 'lazy',  'lacer']) => []
``` 
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def anagrams(word, words):
>    #your code here
>    list_new = [i for i in words if set(i)==set(word)]
>    for j in [i for i in words if set(i)==set(word)]:
>        for k in list(set(word)):
>            if j.count(k)!=word.count(k):
>                list_new.remove(j)
>    return list_new
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def anagrams(word, words): return [item for item in words if sorted(item)==sorted(word)]
>```

></details>

  <img align="right" src="https://media.tenor.com/pIh9_3XzFZIAAAAi/capoo-bug-cat.gif" height="100"/>
  
---
<br>

  
   ## Directions Reduction

**DESCRIPTION:**

  **Once upon a time, on a way through the old wild mountainous west,…**

  … a man was given directions to go from one point to another. The directions were "NORTH", "SOUTH", "WEST", "EAST". Clearly "NORTH" and "SOUTH" are opposite, "WEST" and "EAST" too.

Going to one direction and coming back the opposite direction *right* away is a needless effort. Since this is the wild west, with dreadful weather and not much water, it's important to save yourself some energy, otherwise you might die of thirst!
  
  **How I crossed a *mountainous* desert the smart way.**
  
  The directions given to the man are, for example, the following (depending on the language):
  
```python
["NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST"].
or
{ "NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST" };
or
[North, South, South, East, West, North, West]
```
  
You can immediately see that going "NORTH" and *immediately* "SOUTH" is not reasonable, better stay to the same place! So the task is to give to the man a simplified version of the plan. A better plan in this case is simply:
  
```python
["WEST"]
or
{ "WEST" }
or
[West]
``` 
**Other examples:** 
  
  In ```["NORTH", "SOUTH", "EAST", "WEST"]```, the direction ```"NORTH" + "SOUTH"``` is going north and coming back *right away*.

The path becomes ```["EAST", "WEST"]```, now ```"EAST"``` and ```"WEST"``` annihilate each other, therefore, the final result is ```[]``` (nil in Clojure).

In ["NORTH", "EAST", "WEST", "SOUTH", "WEST", "WEST"], "NORTH" and "SOUTH" are *not* directly opposite but they become directly opposite after the reduction of "EAST" and "WEST" so the whole path is reducible to ["WEST", "WEST"].
  
*Task*  
  
Write a function ```dirReduc``` which will take an array of strings and returns an array of strings with the needless directions removed (W<->E or S<->N *side by side*).
  
* The Haskell version takes a list of directions with ```data Direction = North | East | West | South```.
* The Clojure version returns nil when the path is reduced to nothing.
* The Rust version takes a slice of ```enum Direction {North, East, West, South}```.  
  

 **Notes** 
  
 * Not all paths can be made simpler. The path ["NORTH", "WEST", "SOUTH", "EAST"] is not reducible. "NORTH" and "WEST", "WEST" and "SOUTH", "SOUTH" and "EAST" are not *directly* opposite of each other and can't become such. Hence the result path is itself : ["NORTH", "WEST", "SOUTH", "EAST"].
* if you want to translate, please ask before translating.
  
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def dirReduc(arr):
>
>    d = {1:'NORTH', 2:'SOUTH' , 3:'EAST', 4: 'WEST'}
>    l = []
>    way = (' '.join(arr))
>    while l != way:
>        l = way
>        way = way.replace(d[1]+' '+d[2], '')
>        way = way.replace(d[2]+' '+d[1], '')
>        way = way.replace(d[3]+' '+d[4], '')
>        way = way.replace(d[4]+' '+d[3], '')
>        way = way.replace('  ', ' ')
>        
>    return way.split()
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def dirReduc(arr):
>    dir = " ".join(arr)
>    dir2 = dir.replace("NORTH SOUTH",'').replace("SOUTH NORTH",'').replace("EAST WEST",'').replace("WEST EAST",'')
>    dir3 = dir2.split()
>    return dirReduc(dir3) if len(dir3) < len(arr) else dir3
>```

></details>

---
<br>

  
  
 ## RGB To Hex Conversion


**DESCRIPTION:**

The rgb function is incomplete. Complete it so that passing in RGB decimal values will result in a hexadecimal representation being returned. Valid decimal values for RGB are 0 - 255. Any values that fall out of that range must be rounded to the closest valid value.

Note: Your answer should always be 6 characters long, the shorthand with 3 will not work here.

The following are examples of expected output values:
  
  
```python
rgb(255, 255, 255) # returns FFFFFF
rgb(255, 255, 300) # returns FFFFFF
rgb(0,0,0) # returns 000000
rgb(148, 0, 211) # returns 9400D3
```

  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def rgb(r, g, b):
>    # your code here :)
>    r = 0 if r<0 else r
>    g = 0 if g<0 else g
>    b = 0 if b<0 else b
>    return (('0' + hex(r)[2:].upper())[-2:] if r<=255 else 'FF') +(('0' + hex(g)[2:].upper())[-2:] if g<=255 else 'FF') + (('0' + hex(b)[2:].upper())[-2:] if b<=255 else 'FF')
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def rgb(r, g, b):
>    round = lambda x: min(255, max(x, 0))
>    return ("{:02X}" * 3).format(round(r), round(g), round(b))
>```

></details>

---
<br>


 ## Calculating with Functions

**DESCRIPTION:**

This time we want to write calculations using functions and get the results. Let's have a look at some examples:
  
```python
seven(times(five())) # must return 35
four(plus(nine())) # must return 13
eight(minus(three())) # must return 5
six(divided_by(two())) # must return 3
```
Requirements:
 
  * There must be a function for each number from 0 ("zero") to 9 ("nine")
* There must be a function for each of the following mathematical operations: plus, minus, times, divided_by
* Each calculation consist of exactly one operation and two numbers
* The most outer function represents the left operand, the most inner function represents the right operand
* Division should be integer division. For example, this should return ```2```, not ```2.666666...```:
  
```python
eight(divided_by(three()))
``` 

  
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def zero(a = None): return '0' if a == None else eval('0' + a) #your code here
>def one(a = None): return '1' if a == None else eval('1' + a)#your code here
>def two(a= None): return '2' if a == None else eval('2' + a) #your code here
>def three(a= None): return '3' if a == None else eval('3' + a) #your code here
>def four(a= None): return '4' if a == None else eval('4' + a) #your code here
>def five(a= None): return'5' if a == None else eval('5' + a) #your code here
>def six(a= None): return '6' if a == None else eval('6' + a) #your code here
>def seven(a= None): return '7' if a == None else eval('7' + a) #your code here
>def eight(a= None): return '8' if a == None else eval('8' + a) #your code here
>def nine(a= None): return '9' if a == None else eval('9' + a) #your code here
>
>def plus(b): return '+' + b #your code here
>def minus(b): return '-' + b #your code here
>def times(b): return '*' + b #your code here
>def divided_by(b): return '//' + b #your code here
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def zero(arg=""):  return eval("0" + arg)
>def one(arg=""):   return eval("1" + arg)
>def two(arg=""):   return eval("2" + arg)
>def three(arg=""): return eval("3" + arg)
>def four(arg=""):  return eval("4" + arg)
>def five(arg=""):  return eval("5" + arg)
>def six(arg=""):   return eval("6" + arg)
>def seven(arg=""): return eval("7" + arg)
>def eight(arg=""): return eval("8" + arg)
>def nine(arg=""):  return eval("9" + arg)
>
>def plus(n):       return "+%s" % n
>def minus(n):      return "-%s" % n
>def times(n):      return "*%s" % n
>def divided_by(n): return "/%s" % n
>```

></details>

---
<br>
  
  
   ## Rot13

**DESCRIPTION:**

ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.

Create a function that takes a string and returns the string ciphered with Rot13. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 "implementation".

Please note that using ```encode``` is considered cheating.  

  
<br>
<details><summary>Solution 1</summary> <br>
  
>```python
>def rot13(message):
>    alph_1 = list(map(chr, range(65, 91)))
>    alph_2 = list(map(chr, range(97, 123)))
>    l = []
>    for i in message:
>        if i in alph_1:
>            if (alph_1.index(i) + 13) > 25:
>                l.append(alph_1[(13 - (26 - alph_1.index(i)))])
>            else: l.append(alph_1[alph_1.index(i) + 13])
>        elif i in alph_2:
>            if (alph_2.index(i) + 13) > 25:
>                l.append(alph_2[(13 - (26 - alph_2.index(i)))])
>            else: l.append(alph_2[alph_2.index(i) + 13])
>        else: l.append(i)
>    return ''.join(l)  
>```
</details><br>


<details><summary>Solution 2</summary><br>

>```python
>def rot13(message):
>    alph_1 = list(map(chr, range(65, 91)))+list(map(chr, range(65, 91)))
>    alph_2 = list(map(chr, range(97, 123)))+list(map(chr, range(97, 123)))
>    l = []
>    for i in message:
>        if i in alph_1:
>                l.append(alph_1[alph_1.index(i)+13])
>        elif i in alph_2:
>                l.append(alph_2[alph_2.index(i)+13])
>        else: l.append(i)
>    return ''.join(l)  
>```

></details><br>
  
  
  <details><summary>Solution 3</summary><br>

>```python
>def rot13(message):
>    alph_1 = list(map(chr, range(65, 91)))
>    alph_2 = list(map(chr, range(97, 123)))
>    l = []
>    for i in message:
>        if i in alph_1:
>                l.append(alph_1[(alph_1.index(i)+13)%26])
>        elif i in alph_2:
>                l.append(alph_2[(alph_2.index(i)+13)%26])
>        else: l.append(i)
>    return ''.join(l)    
>```

></details><br>
  
    
  <details><summary>Favorite solution</summary><br>

>```python
>def rot13(message):
>    return message.translate(message.maketrans('ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz','NOPQRSTUVWXYZABCDEFGHIJKLMnopqrstuvwxyzabcdefghijklm'))
>```

></details>

  <img align="right" src="https://media.tenor.com/4xobbChP2c4AAAAi/capoo-bugcat.gif" height="100"/>
  
---
<br>
  
  
  
   ## Maximum subarray sum

**DESCRIPTION:**

  The maximum sum subarray problem consists in finding the maximum sum of a contiguous subsequence in an array or list of integers:
  
```python
max_sequence([-2, 1, -3, 4, -1, 2, 1, -5, 4])
# should be 6: [4, -1, 2, 1]
```
  
Easy case is when the list is made up of only positive numbers and the maximum sum is the sum of the whole array. If the list is made up of only negative numbers, return 0 instead.

Empty list is considered to have zero greatest sum. Note that the empty list or array is also a valid sublist/subarray.
   
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def max_sequence(arr):
>    l_sum = []
>    l_sum_max = []
>    for i in arr:
>        l_sum.append(i)
>        if sum(l_sum)>sum(l_sum_max):
>            l_sum_max = l_sum.copy()
>        if sum(l_sum)<0:
>            l_sum = []
>    return sum(l_sum_max)
>```
</details><br>


<details><summary>Favorite solution 1</summary><br>

>```python
>def maxSequence(arr):
>    max,curr=0,0
>    for x in arr:
>        curr+=x
>        if curr<0:curr=0
>        if curr>max:max=curr
>    return max
>```

></details><br> 

<details><summary>Favorite solution 2</summary><br> 
  
>```python
>def maxSequence(arr):
>    return max([sum(arr[i:j]) for i in range(len(arr)+1) for j in range(len(arr)+1)])
>```

></details> 
  
---
<br>
  
  
  
  
   ## Product of consecutive Fib numbers

**DESCRIPTION:**

  The Fibonacci numbers are the numbers in the following integer sequence (Fn):
  
  > *"0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, ..."*
  
  such as
  
  > *"F(n) = F(n-1) + F(n-2) with F(0) = 0 and F(1) = 1."*
  
  Given a number, say prod (for product), we search two Fibonacci numbers F(n) and F(n+1) verifying
  
  > *"F(n) * F(n+1) = prod."*
  
  Your function productFib takes an integer (prod) and returns an array:
  
  ```[F(n), F(n+1), true] or {F(n), F(n+1), 1} or (F(n), F(n+1), True)```
  
  depending on the language if F(n) * F(n+1) = prod.

If you don't find two consecutive F(n) verifying ```F(n) * F(n+1) = prod``` you will return
  
  ```[F(n), F(n+1), false] or {F(n), F(n+1), 0} or (F(n), F(n+1), False)```
  
  F(n) being the smallest one such as ```F(n) * F(n+1) > prod```.
  
  **Some Examples of Return:**
  
  (depend on the language)
  
```python
productFib(714) # should return (21, 34, true), 
                # since F(8) = 21, F(9) = 34 and 714 = 21 * 34

productFib(800) # should return (34, 55, false), 
                # since F(8) = 21, F(9) = 34, F(10) = 55 and 21 * 34 < 800 < 34 * 55
-----
productFib(714) # should return [21, 34, true], 
productFib(800) # should return [34, 55, false], 
-----
productFib(714) # should return {21, 34, 1}, 
productFib(800) # should return {34, 55, 0},        
-----
productFib(714) # should return {21, 34, true}, 
productFib(800) # should return {34, 55, false}, 
``` 
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def productFib(prod):
>    list_fib=[0, 1]
>    list_prod=[0]
>    while list_prod[-1] < prod:
>        list_fib.append(list_fib[-1]+list_fib[-2])
>        list_prod.append(list_fib[-2]*list_fib[-1])
>    return [list_fib[-2], list_fib[-1],list_fib[-2]*list_fib[-1]== prod]
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def productFib(prod):
>  a, b = 0, 1
>  while prod > a * b:
>    a, b = b, a + b
>  return [a, b, prod == a * b]
>```

></details>

---
<br>
  
  
  
   ## Pete, the baker

**DESCRIPTION:**

  Pete likes to bake some cakes. He has some recipes and ingredients. Unfortunately he is not good in maths. Can you help him to find out, how many cakes he could bake considering his recipes?

Write a function ```cakes()```, which takes the recipe (object) and the available ingredients (also an object) and returns the maximum number of cakes Pete can bake (integer). For simplicity there are no units for the amounts (e.g. 1 lb of flour or 200 g of sugar are simply 1 or 200). Ingredients that are not present in the objects, can be considered as 0.

Examples:
  
```python
# must return 2
cakes({flour: 500, sugar: 200, eggs: 1}, {flour: 1200, sugar: 1200, eggs: 5, milk: 200})
# must return 0
cakes({apples: 3, flour: 300, sugar: 150, milk: 100, oil: 100}, {sugar: 500, flour: 2000, milk: 2000})
```

<br>
<details><summary>My Solution 1</summary> <br>
  
>```python
>def cakes(recipe, available):
>    for j in list(recipe.keys()):
>        if j not in list(available.keys()):
>            return 0 
>    else: return min([(available[i]//recipe[i]) for i in list(recipe.keys())])
>```
</details><br>
  
  <details><summary>My Solution 2</summary> <br>
  
>```python
>def cakes(recipe, available):
>    return min([(available[i]//recipe[i]) if i in available else 0  for i in recipe ])
>```
</details><br>


<details><summary>Favorite solution 1</summary><br>

>```python
>def cakes(recipe, available):
>    return min(available.get(k, 0)/recipe[k] for k in recipe)
>```

></details><br>

  <details><summary>Favorite solution 2</summary><br>

>```python
>def cakes(recipe, available):
>    try:
>        return min([available[a]/recipe[a] for a in recipe])
>    except:
>        return 0
>```

></details>
  
---
<br>

  
  ## The Hashtag Generator

**DESCRIPTION:**

The marketing team is spending way too much time typing in hashtags.
Let's help them with our own Hashtag Generator!

Here's the deal:

* It must start with a hashtag (```#```).
* All words must have their first letter capitalized.
* If the final result is longer than 140 chars it must return ```false```.
* If the input or the result is an empty string it must return ```false```.
  
**Examples**  
  
```python
" Hello there thanks for trying my Kata"  =>  "#HelloThereThanksForTryingMyKata"
"    Hello     World   "                  =>  "#HelloWorld"
""                                        =>  false
```

  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def generate_hashtag(s):
>    #your code here
>    if len(s) >= 140 or s == '':
>        return False
>    else: return '#' + ''.join([i.title() for i in s.split()])
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def generate_hashtag(s):
>    return '#' +s.strip().title().replace(' ','') if 0<len(s)<=140 else False
>```

></details>

  <img align="right" src="https://media.tenor.com/cC7_rNf-BrQAAAAi/capoo-bugcat.gif" height="100"/>
  
---
<br>

  
  ## Weight for weight

**DESCRIPTION:**

 My friend John and I are members of the "Fat to Fit Club (FFC)". John is worried because each month a list with the weights of members is published and each month he is the last on the list which means he is the heaviest.

I am the one who establishes the list so I told him: "Don't worry any more, I will modify the order of the list". It was decided to attribute a "weight" to numbers. The weight of a number will be from now on the sum of its digits.

For example ```99``` will have "weight" ```18```, ```100``` will have "weight" ```1``` so in the list ```100``` will come before ```99```.

Given a string with the weights of FFC members in normal order can you give this string ordered by "weights" of these numbers? 
  
**Example:**  
  
  
```python
"56 65 74 100 99 68 86 180 90" ordered by numbers weights becomes: 

"100 180 90 56 65 74 68 86 99"
```

When two numbers have the same "weight", let us class them as if they were strings (alphabetical ordering) and not numbers:

```180``` is before ```90``` since, having the same "weight" (*9*), it comes before as a *string*.

All numbers in the list are positive numbers and the list can be empty.
  
  **Notes**
  
* it may happen that the input string have leading, trailing whitespaces and more than a unique whitespace between two consecutive numbers
* For C: The result is freed.
  

<br>
<details><summary>My Solution 1 </summary> <br>
  
>```python
>def order_weight(strng):
>    l = sorted(strng.split())
>    fat = [sum([int(k) for k in j]) for j in l]
>    fat_sort = sorted(fat)
>    ind = [fat.index(h) for h in fat_sort]
>    m = []
>    for y in sorted(fat):
>        m.append(fat.index(y))
>        fat[fat.index(y)] = 'None'
>    return ' '.join([l[s] for s in m])  
>```
</details><br>
  
  <details><summary>My Solution 2 </summary> <br>
  
>```python
>def order_weight(strng):
>    l = sorted(strng.split())
>    # k = [sum([int(j) for j in i]) for i in l]
>    return ' '.join(sorted(l, key = lambda l: sum(int(j) for j in l)))    
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def order_weight(_str):
>    return ' '.join(sorted(sorted(_str.split(' ')), key=lambda x: sum(int(c) for c in x)))
>```

></details>

---
<br>

  
  
  ## First non-repeating character

**DESCRIPTION:**

  Write a function named ```first_non_repeating_letter``` that takes a string input, and returns the first character that is not repeated anywhere in the string.

For example, if given the input ```'stress'```, the function should return ```'t'```, since the letter t only occurs once in the string, and occurs first in the string.

As an added challenge, upper- and lowercase letters are considered the **same character**, but the function should return the correct case for the initial letter. For example, the input ```'sTreSS'``` should return ```'T'```.

If a string contains *all repeating characters*, it should return an empty string (```""```) or ```None``` -- see sample tests.
  
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def first_non_repeating_letter(string):
>    #your code here
>    st = ''.join([i for i in string if string.lower().count(i.lower()) == 1])
>    return st[0] if st!='' else st
>```
</details>
  
---
<br>

  
  
  ## String incrementer

**DESCRIPTION:**

 Your job is to write a function which increments a string, to create a new string.

* If the string already ends with a number, the number should be incremented by 1.
* If the string does not end with a number. the number 1 should be appended to the new string.
  
 Examples:
  
```python
foo -> foo1

foobar23 -> foobar24

foo0042 -> foo0043

foo9 -> foo10

foo099 -> foo100
```

*Attention: If the number has leading zeros the amount of digits should be considered.*

  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def increment_string(strng):
>    
>    if strng == '' or strng[-1] not in '0123456789':
>        return strng + '1'
>    else:
>        s = ''
>        l = [j for j in strng]
>        while len(l)>0:
>            if l[-1] in '0123456789':
>                s += l[-1]
>                l.pop(-1)
>            else: break
>        itog = str(int(s[::-1])+1)
>        return (''.join(l) + (len(s) - len(itog))*'0' + itog)
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def increment_string(strng):
>    head = strng.rstrip('0123456789')
>    tail = strng[len(head):]
>    if tail == "": return strng+"1"
>    return head + str(int(tail) + 1).zfill(len(tail))
>```

></details>

  <img align="right" src="https://media.tenor.com/P3yMAjqZBmIAAAAi/capoo-blue.gif" height="100"/>
  
---
<br>
 
  
  ## Extract the domain name from a URL

**DESCRIPTION:**

  Write a function that when given a URL as a string, parses out just the domain name and returns it as a string. For example:
  
```python
* url = "http://github.com/carbonfive/raygun" -> domain name = "github"
* url = "http://www.zombie-bites.com"         -> domain name = "zombie-bites"
* url = "https://www.cnet.com"                -> domain name = cnet"
```

  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def domain_name(url):
>      url = url.split('.')
>    if url[0].lstrip('htps:/w'):
>        return url[0].split('//')[1] if len(url[0].split('//'))>1 else url[0]
>    else: return url[1]
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def domain_name(url):
>    return url.split("//")[-1].split("www.")[-1].split(".")[0]
>```

></details>

---
<br>

  
  ## Scramblies

**DESCRIPTION:**

Complete the function ```scramble(str1, str2)``` that returns ```true``` if a portion of ```str1``` characters can be rearranged to match ```str2```, otherwise returns ```false```.

**Notes:**

* Only lower case letters will be used (a-z). No punctuation or digits will be included.
* Performance needs to be considered.
  
**Examples**
  
```python
scramble('rkqodlw', 'world') ==> True
scramble('cedewaraaossoqqyt', 'codewars') ==> True
scramble('katas', 'steak') ==> False
```
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def scramble(s1, s2):
>    for i in set(s2):
>        if not (set(s2).issubset(s1) and s2.count(i) <= s1.count(i)):
>            return False
>    return True
>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python
>def scramble(s1, s2):
>    return not any(s1.count(char) < s2.count(char) for char in set(s2))
>```

></details>

---
<br>

  
  
  ## Number of trailing zeros of N!

**DESCRIPTION:**

  Write a program that will calculate the number of trailing zeros in a factorial of a given number.

```N! = 1 * 2 * 3 *  ... * N```

Be careful ```1000!``` has 2568 digits...
  
 **Examples** 
  
  
```python
zeros(6) = 1
# 6! = 1 * 2 * 3 * 4 * 5 * 6 = 720 --> 1 trailing zero

zeros(12) = 2
# 12! = 479001600 --> 2 trailing zeros
```
  
Hint: You're not meant to calculate the factorial. Find another way to find the number of zeros.
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def zeros(n):
>    sum = 0
>    for i in range(1, 1000):
>        sum += n//(5**i)
>    return sum
>```
</details><br>


<details><summary>Favorite solution 1</summary><br>

>```python
>def zeros(n):
>    zeros = 0
>    i = 5
>    while n//i > 0:
>        zeros += n//i
>        i *= 5
>    return zeros
>```

></details><br>
  
 <details><summary>Favorite solution 2</summary><br>

>```python
>def zeros(n):
>  x = n//5
>  return x + zeros(x) if x else 0
>```

></details>

---
<br>

  
  
  ## Greed is Good


**DESCRIPTION:**

  Greed is a dice game played with five six-sided dice. Your mission, should you choose to accept it, is to score a throw according to these rules. You will always be given an array with five six-sided dice values.
  
  
```python
 Three 1's => 1000 points
 Three 6's =>  600 points
 Three 5's =>  500 points
 Three 4's =>  400 points
 Three 3's =>  300 points
 Three 2's =>  200 points
 One   1   =>  100 points
 One   5   =>   50 point
```

A single die can only be counted once in each roll. For example, a given "5" can only count as part of a triplet (contributing to the 500 points) or as a single 50 points, but not both in the same roll.

Example scoring
  
  
```python
 Throw       Score
 ---------   ------------------
 5 1 3 4 1   250:  50 (for the 5) + 2 * 100 (for the 1s)
 1 1 1 3 1   1100: 1000 (for three 1s) + 100 (for the other 1)
 2 4 4 5 4   450:  400 (for three 4s) + 50 (for the 5)
``` 

 In some languages, it is possible to mutate the input to the function. This is something that you should never do. If you mutate the input, you will not be able to pass all the tests. 
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python
>def score(dice):
>    # your code here
>    dict_trow = {1:1000, 6:600, 5:500, 4:400, 3:300, 2:200}
>    dict_one = {1:100, 5:50}
>    l1 = [dict_trow[i] for i in set(dice) if dice.count(i)>=3]
>    l2 = [(dice.count(j)-3)*dict_one[j] for j in set(dice) if (j == 1 or j ==5) and dice.count(j)>=3]
>    l3 = [(dice.count(j))*dict_one[j] for j in set(dice) if (j == 1 or j ==5) and dice.count(j)<3]
>    return sum(l1+l2+l3)
>```
</details><br>


<details><summary>Favorite solution 1</summary><br>

>```python
>def score(dice):
>    return dice.count(1)//3 * 1000 + dice.count(1)%3 * 100 \
>           + dice.count(2)//3 * 200 \
>           + dice.count(3)//3 * 300 \
>           + dice.count(4)//3 * 400 \
>           + dice.count(5)//3 * 500 + dice.count(5)%3 * 50 \
>           + dice.count(6)//3 * 600 \
>```

></details>
<img align="right" src="https://media.tenor.com/MKU57hv9JkwAAAAi/capoo-bugcat.gif" height="100"/>
  
---
<br>

  
  
  ## <title of the challenge>

**DESCRIPTION:**

  
```python

```

  
```python

``` 

  
  
<br>
<details><summary>My Solution</summary> <br>
  
>```python

>```
</details><br>


<details><summary>Favorite solution</summary><br>

>```python

>```

></details>

---
<br>















