# Python Cheatsheet

## Data Types

```python
# Integers and floats
x = 42
y = 3.14
z = 1_000_000          # Underscore separator for readability

# Strings
s = "Hello, World!"
s2 = 'Single quotes work too'
s3 = """Multi-line
string"""
raw = r"Raw string\n"  # No escape processing

# Booleans
t = True
f = False

# None
n = None

# Type checking and conversion
type(x)                # <class 'int'>
isinstance(x, int)     # True
int("42")              # 42
float("3.14")          # 3.14
str(42)                # "42"
bool(0)                # False
```

## Strings

```python
s = "Hello, World!"
len(s)                 # 13
s.upper()              # "HELLO, WORLD!"
s.lower()              # "hello, world!"
s.strip()              # Remove leading/trailing whitespace
s.lstrip()             # Remove leading whitespace
s.rstrip()             # Remove trailing whitespace
s.replace("l", "r")   # "Herro, Worrd!"
s.split(", ")          # ["Hello", "World!"]
", ".join(["a", "b"])  # "a, b"
s.startswith("Hello") # True
s.endswith("!")        # True
s.find("World")        # 7 (index), -1 if not found
s.count("l")           # 3
s[0]                   # "H"
s[7:12]                # "World"
s[:5]                  # "Hello"
s[-1]                  # "!"
s[::-1]                # Reversed string

# Formatting
name = "Alice"
age = 30
f"Hello, {name}! You are {age}."       # f-string (Python 3.6+)
"Hello, {}! You are {}.".format(name, age)
"Hello, %s! You are %d." % (name, age)
```

## Lists

```python
lst = [1, 2, 3, 4, 5]
lst[0]                 # 1
lst[-1]                # 5
lst[1:3]               # [2, 3]
lst.append(6)          # Add to end
lst.insert(0, 0)       # Insert at index
lst.extend([7, 8])     # Extend with another list
lst.remove(3)          # Remove first occurrence of value
lst.pop()              # Remove and return last element
lst.pop(0)             # Remove and return element at index
lst.index(2)           # Find index of value
lst.count(1)           # Count occurrences
lst.sort()             # Sort in-place
lst.sort(reverse=True) # Sort descending
sorted(lst)            # Return new sorted list
lst.reverse()          # Reverse in-place
len(lst)               # Length
2 in lst               # True (membership test)

# List comprehension
squares = [x**2 for x in range(10)]
evens = [x for x in range(20) if x % 2 == 0]
```

## Tuples

```python
t = (1, 2, 3)
t[0]                   # 1 (indexed access)
a, b, c = t            # Unpacking
a, *rest = t           # Extended unpacking: a=1, rest=[2,3]
t + (4, 5)             # Concatenation: (1, 2, 3, 4, 5)
len(t)                 # 3
```

## Dictionaries

```python
d = {"name": "Alice", "age": 30}
d["name"]              # "Alice"
d.get("age")           # 30
d.get("missing", 0)    # 0 (default value)
d["city"] = "Paris"    # Add/update key
del d["age"]           # Delete key
d.keys()               # dict_keys(["name", "city"])
d.values()             # dict_values(["Alice", "Paris"])
d.items()              # dict_items([("name", "Alice"), ...])
"name" in d            # True
d.update({"x": 1})     # Merge another dict
d.pop("x")             # Remove and return value
d.setdefault("y", 0)   # Set if missing, return value

# Dict comprehension
squares = {x: x**2 for x in range(5)}
```

## Sets

```python
s = {1, 2, 3, 4}
s.add(5)               # Add an element
s.remove(3)            # Remove (raises KeyError if missing)
s.discard(3)           # Remove (no error if missing)
s.union({5, 6})        # s | {5, 6}
s.intersection({2, 3}) # s & {2, 3}
s.difference({2, 3})   # s - {2, 3}
s.symmetric_difference({3, 5})  # s ^ {3, 5}
2 in s                 # True
```

## Control Flow

```python
# If/elif/else
if x > 0:
    print("positive")
elif x < 0:
    print("negative")
else:
    print("zero")

# Ternary
result = "yes" if condition else "no"

# For loop
for i in range(10):
    print(i)

for index, value in enumerate(lst):
    print(index, value)

for key, value in d.items():
    print(key, value)

# While loop
while condition:
    do_something()

# Loop control
break      # Exit loop
continue   # Skip to next iteration
else:      # Runs if loop wasn't broken
```

## Functions

```python
def greet(name, greeting="Hello"):
    """Docstring here."""
    return f"{greeting}, {name}!"

# Variable arguments
def func(*args, **kwargs):
    print(args)    # Tuple of positional args
    print(kwargs)  # Dict of keyword args

# Lambda
square = lambda x: x ** 2

# Type hints (Python 3.5+)
def add(a: int, b: int) -> int:
    return a + b
```

## Classes

```python
class Animal:
    species = "Unknown"                    # Class variable

    def __init__(self, name: str) -> None:
        self.name = name                   # Instance variable

    def speak(self) -> str:
        return f"{self.name} makes a sound"

    @classmethod
    def create(cls, name: str) -> "Animal":
        return cls(name)

    @staticmethod
    def info() -> str:
        return "I am an animal"

    def __repr__(self) -> str:
        return f"Animal(name={self.name!r})"


class Dog(Animal):                         # Inheritance
    def speak(self) -> str:
        return f"{self.name} barks"
```

## Error Handling

```python
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"Error: {e}")
except (TypeError, ValueError):
    print("Type or value error")
else:
    print("No error occurred")
finally:
    print("Always runs")

# Raising exceptions
raise ValueError("Invalid value")

# Custom exception
class MyError(Exception):
    pass
```

## File I/O

```python
# Reading
with open("file.txt", "r") as f:
    content = f.read()

with open("file.txt") as f:
    lines = f.readlines()       # List of lines

with open("file.txt") as f:
    for line in f:              # Iterate line by line
        print(line.strip())

# Writing
with open("file.txt", "w") as f:
    f.write("Hello\n")

with open("file.txt", "a") as f:  # Append mode
    f.write("More content\n")
```

## Useful Built-ins

```python
len(x)               # Length
range(10)            # 0 to 9
range(1, 11)         # 1 to 10
range(0, 10, 2)      # 0, 2, 4, 6, 8
zip([1,2], ['a','b'])  # [(1,'a'), (2,'b')]
map(str, [1, 2, 3])  # Lazy map
filter(None, lst)    # Filter falsy values
sum([1, 2, 3])       # 6
min([3, 1, 2])       # 1
max([3, 1, 2])       # 3
abs(-5)              # 5
round(3.14159, 2)    # 3.14
sorted(lst, key=lambda x: x[1])  # Sort by second element
any([False, True])   # True
all([True, True])    # True
```

## Common Standard Library

```python
import os
os.getcwd()              # Current directory
os.listdir(".")          # List directory
os.path.join(a, b)       # Join paths
os.path.exists(path)     # Check if path exists
os.makedirs(path)        # Create directories

import sys
sys.argv                 # Command line arguments
sys.exit(0)              # Exit with status code

import json
json.dumps({"a": 1})     # Serialize to JSON string
json.loads('{"a": 1}')  # Parse JSON string

import re
re.match(r"\d+", "123abc")   # Match at start
re.search(r"\d+", "abc123")  # Match anywhere
re.findall(r"\d+", "1a2b3")  # All matches: ["1", "2", "3"]
re.sub(r"\d+", "X", "a1b2")  # Substitute: "aXbX"

from datetime import datetime, timedelta
now = datetime.now()
today = datetime.today().date()
delta = timedelta(days=7)
next_week = now + delta

from pathlib import Path
p = Path(".")
p.glob("**/*.py")        # Find Python files
(p / "subdir" / "file.txt").read_text()
```
