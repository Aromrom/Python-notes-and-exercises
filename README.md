# **Python-notes-and-exercises**
# 🔢 Integers

## 🔹 Basics

```python
x = 42
y = -7
z = 1_000_000    # underscores for readability
```
Integers in Python have arbitrary precision (limited by memory, not 32/64 bits).
##🔹 Common Operations
```python
x + y   # addition
x - y   # subtraction
x * y   # multiplication
x / y   # float division
x // y  # floor division (integer result)
x % y   # modulus (remainder)
x ** y  # exponentiation
divmod(x, y)  # (quotient, remainder)
```
🔹 Useful Built-ins
```python
abs(-42)        # 42
pow(2, 5)       # 32
pow(2, 5, 3)    # (2^5) % 3 = 2
round(3.14159)  # 3
int("123")      # convert string to int
bin(42)         # '0b101010'
hex(42)         # '0x2a'
oct(42)         # '0o52'
```
🔹 Comparisons & Checks
```python
x == y     # equality
x != y     # inequality
x > y      # greater
x < y      # less
x >= y     # greater or equal
x <= y     # less or equal

isinstance(x, int)   # True if x is an int
```
🔹 Bitwise Operations
```python
x & y   # bitwise AND
x | y   # bitwise OR
x ^ y   # bitwise XOR
~x      # bitwise NOT
x << 2  # shift left (multiply by 2^2)
x >> 2  # shift right (divide by 2^2)
```
🔹 Common Integer Algorithms
✅ FizzBuzz
```python
for i in range(1, 21):
    if i % 15 == 0:
        print("FizzBuzz")
    elif i % 3 == 0:
        print("Fizz")
    elif i % 5 == 0:
        print("Buzz")
    else:
        print(i)
```
✅ Fibonacci Sequence
```python
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        print(a, end=" ")
        a, b = b, a + b

fibonacci(10)  # 0 1 1 2 3 5 8 13 21 34
```
✅ Prime Check
```python
def is_prime(n):
    if n < 2: return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True
```
✅ Factorial
```python
def factorial(n):
    return 1 if n == 0 else n * factorial(n-1)

print(factorial(5))  # 120
```
✅ GCD & LCM
```python
import math
math.gcd(48, 18)   # 6
math.lcm(48, 18)   # 144
```
🔹 Integer Tricks
```python
# Swap values
a, b = 5, 10
a, b = b, a   # now a=10, b=5

# Reverse an integer
num = 12345
rev = int(str(num)[::-1])   # 54321

# Armstrong number check (e.g., 153 = 1³+5³+3³)
n = 153
print(n == sum(int(d)**3 for d in str(n)))
```
## 🔤 Strings

🔹 Basics
```python
s1 = "Hello"
s2 = 'World'
s3 = """This is
a multi-line string"""
s4 = 'It\'s Python'  # escape character
```
-Strings are immutable in Python.
-Can use single ', double ", or triple """ for multi-line strings.

🔹 Common Operations
```python
# Concatenation
s = s1 + " " + s2       # "Hello World"

# Repetition
s = s1 * 3               # "HelloHelloHello"

# Indexing
s1[0]     # 'H'
s1[-1]    # 'o'

# Slicing
s1[1:4]   # 'ell'   (start inclusive, end exclusive)
s1[:3]    # 'Hel'
s1[2:]    # 'llo'
s1[:]     # 'Hello' (copy of string)
```
🔹 Common Methods
```python
s = "  Python  "

# Case
s.upper()      # '  PYTHON  '
s.lower()      # '  python  '
s.title()      # '  Python  '
s.capitalize() # '  python  '

# Strip
s.strip()      # 'Python'       (remove whitespace)
s.lstrip()     # 'Python  '
s.rstrip()     # '  Python'

# Replace & Split
s.replace("Python", "Java")  # '  Java  '
s.split()                    # ['Python']
s.split("y")                 # [' P', 'thon']

# Join
"-".join(["a","b","c"])      # 'a-b-c'

# Find & Count
s.find("Py")   # 2 (index) or -1 if not found
s.count("o")   # 1

# Check
s.isalpha()    # False (has spaces)
s.isdigit()    # False
s.islower()    # False
s.isupper()    # False
s.startswith("Py")  # True
s.endswith("on")    # True
```
🔹 Common String Algorithms
✅ Palindrome Check
```python
def is_palindrome(s):
    s = s.lower().replace(" ", "")
    return s == s[::-1]

print(is_palindrome("Race car"))  # True
```
✅ Reverse Words in a Sentence
```python
sentence = "Hello World from Python"
print(" ".join(sentence.split()[::-1]))
# Output: "Python from World Hello"
```
✅ Count Vowels
```python
def count_vowels(s):
    return sum(1 for c in s.lower() if c in "aeiou")

print(count_vowels("Python"))  # 1
```
✅ Remove Duplicates
```python
s = "banana"
print("".join(sorted(set(s), key=s.index)))  # 'ban'
```
✅ Anagram Check
```python
def are_anagrams(s1, s2):
    return sorted(s1.replace(" ", "").lower()) == sorted(s2.replace(" ", "").lower())

print(are_anagrams("Listen", "Silent"))  # True
```
🔹 Escape Sequences
```python
\n   # newline
\t   # tab
\\   # backslash
\'   # single quote
\"   # double quote
```
🔹 Tricks & Tips
```python
# Repeat character n times
"-"*10   # '----------'

# Center / justify strings
s.center(20, "*")   # '*******Python*******'
s.ljust(20, "-")    # 'Python--------------'
s.rjust(20, "-")    # '--------------Python'

# Check if string is numeric
"123".isnumeric()   # True
"-123".lstrip('-').isnumeric()  # True
```
## 📄 Lists
🔹 Basics
```python
lst = [1, 2, 3, 4, 5]
lst2 = ["apple", "banana", "cherry"]
lst3 = [1, "two", 3.0, [4, 5]]  # mixed types allowed
empty = []
```
-Lists are mutable (you can change, add, or remove elements).
-Can contain any type, including other lists.
🔹 Common Operations
```python
# Indexing
lst[0]     # 1
lst[-1]    # 5

# Slicing
lst[1:4]   # [2, 3, 4]
lst[:3]    # [1, 2, 3]
lst[2:]    # [3, 4, 5]
lst[:]     # [1, 2, 3, 4, 5] (copy)

# Length
len(lst)   # 5

# Concatenation & Repetition
lst + [6, 7]  # [1,2,3,4,5,6,7]
lst * 2       # [1,2,3,4,5,1,2,3,4,5]

# Membership
3 in lst     # True
10 not in lst # True
```
🔹 Common Methods
```python
lst.append(6)       # add single element at end
lst.extend([7,8])   # add multiple elements
lst.insert(2, 99)   # insert 99 at index 2

lst.remove(2)       # remove first occurrence of value 2
lst.pop()           # remove last element and return it
lst.pop(1)          # remove element at index 1
del lst[0]          # delete by index
lst.clear()         # remove all elements

lst.index(3)        # find first index of 3
lst.count(2)        # count occurrences of 2

lst.sort()          # sort ascending
lst.sort(reverse=True)  # descending
sorted(lst)         # returns sorted copy
lst.reverse()       # reverse in place
```
🔹 List Comprehensions
```python
# Squares of numbers
squares = [x**2 for x in range(1, 6)]  # [1,4,9,16,25]

# Even numbers
evens = [x for x in range(10) if x % 2 == 0]

# Flatten a 2D list
matrix = [[1,2],[3,4]]
flat = [num for row in matrix for num in row]  # [1,2,3,4]

# Conditional transformation
nums = [1,2,3,4]
modified = [x*2 if x%2==0 else x*3 for x in nums]  # [3,4,9,8]
```
🔹 Common List Algorithms
✅ Reverse a List
```python
lst[::-1]        # slicing
lst.reverse()    # in-place
```
✅ Find Maximum/Minimum
```python
max(lst)  # largest element
min(lst)  # smallest element
```
✅ Sum / Product
```python
sum(lst)                   # sum of elements
import math
math.prod(lst)             # product of elements
```
✅ Remove Duplicates
```python
lst = [1,2,2,3,4,4,5]
unique = list(dict.fromkeys(lst))  # [1,2,3,4,5] preserves order
```
✅ Flatten Nested Lists
```python
nested = [[1,2], [3,4], [5]]
flat = [x for sub in nested for x in sub]  # [1,2,3,4,5]
```
✅ List Rotation
```python
# Rotate right by 2
lst = [1,2,3,4,5]
n = 2
rotated = lst[-n:] + lst[:-n]  # [4,5,1,2,3]
```
🔹 Tricks & Tips
```python
# Swap elements
lst[0], lst[1] = lst[1], lst[0]

# Copy list
lst_copy = lst[:]         # slicing
lst_copy = list(lst)      # constructor
lst_copy = lst.copy()     # copy method

# Merge lists
lst_merged = lst + [6,7,8]

# Multiply elements
doubled = [x*2 for x in lst]
```
## 📑 Tuples
🔹 Basics
```python
t = (1, 2, 3, 4, 5)
t2 = ("apple", "banana", "cherry")
t3 = (1, "two", 3.0, [4, 5])  # mixed types
single = (42,)   # note the trailing comma!
empty = ()       # empty tuple
```
-Tuples are immutable (cannot be changed after creation).
-Faster than lists and often used for fixed data.
🔹 Common Operations
```python
t[0]     # 1
t[-1]    # 5

t[1:4]   # (2, 3, 4)
t[:3]    # (1, 2, 3)
t[2:]    # (3, 4, 5)

len(t)   # 5
3 in t   # True
10 not in t  # True

t + (6, 7)   # (1,2,3,4,5,6,7)
t * 2        # (1,2,3,4,5,1,2,3,4,5)
```
🔹 Tuple Packing & Unpacking
```python
# Packing
point = (3, 4)

# Unpacking
x, y = point
print(x, y)  # 3 4

# Swap variables
a, b = 5, 10
a, b = b, a   # a=10, b=5

# Extended unpacking
t = (1, 2, 3, 4, 5)
a, *b, c = t
print(a, b, c)  # 1 [2,3,4] 5
```
🔹 Built-in Functions
```python
max(t)    # largest element
min(t)    # smallest element
sum(t)    # sum of elements
sorted(t) # returns a sorted list
tuple([1,2,3])  # convert list to tuple
list(t)   # convert tuple to list
```
🔹 Tuple Methods
```python
t.count(2)   # count occurrences of 2
t.index(3)   # index of first occurrence of 3
```
🔹 Common Use Cases
✅ Return Multiple Values from a Function
```python
def min_max(nums):
    return min(nums), max(nums)

lo, hi = min_max([3, 7, 2, 9])
print(lo, hi)  # 2 9
```
✅ Store Immutable Data
```python
# Coordinates, database records, etc.
point = (10, 20)
rgb = (255, 128, 64)
```
✅ Use as Dictionary Keys (Immutable!)
```python
locations = {
    (40.7128, -74.0060): "New York",
    (34.0522, -118.2437): "Los Angeles"
}
```
🔹 Tricks & Tips
```python
# Nested tuples
nested = ((1,2), (3,4), (5,6))

# Flatten nested tuples into list
flat = [x for tup in nested for x in tup]  # [1,2,3,4,5,6]

# Check immutability
t = (1, 2, [3, 4])
t[2][0] = 99   # Works! (list inside tuple is mutable)
```
✅ Tuples are immutable, lightweight, and hashable (can be dict keys), which makes them super handy for safe, fixed collections of data.
---
---

Thank you for checking out this guide! 🙌
