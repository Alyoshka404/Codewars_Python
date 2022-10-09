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
























