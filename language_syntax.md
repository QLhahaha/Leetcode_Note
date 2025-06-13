# Language Syntax

## Python

## 0. General
### mutable vs immutable
- immutable: strings, tuples, frozensets
- mutable: lists, sets, dictionaries

## 1. Basic Syntax
### 1.1 Variable Assignment & Types
```python
# Multiple assignment
a, b, c = 1, 2, 3
x = y = z = 0

# Type hints (Python 3.5+)
name: str = "Alice"
numbers: List[int] = [1, 2, 3]
```

### 1.2 String Formatting
```python
# f-strings (Python 3.6+)
name = "Alice"
age = 25
print(f"Hello {name}, you are {age} years old")

# Format method
print("Hello {}, you are {} years old".format(name, age))
print("Hello {name}, you are {age} years old".format(name=name, age=age))
```

## 2. Control Structures
### 2.1 Conditional Expressions
```python
# Ternary operator
result = "pass" if score >= 60 else "fail"

# Walrus operator (Python 3.8+)
if (n := len(data)) > 10:
    print(f"Large dataset with {n} items")
```

### 2.2 Loop Patterns
```python
# Enumerate with start
for i, item in enumerate(items, start=1):
    print(f"{i}: {item}")

# Zip multiple iterables
names = ["Alice", "Bob"]
ages = [25, 30]
for name, age in zip(names, ages):
    print(f"{name} is {age}")

# Dictionary iteration
for key, value in dict.items():
    print(f"{key}: {value}")
```


## 3. Data Structure
### 3.1 List Comprehensions
```python
# Basic list comprehension
squares = [x**2 for x in range(10)]

# With condition
evens = [x for x in range(20) if x % 2 == 0]

# Nested comprehension
matrix = [[i*j for j in range(3)] for i in range(3)]
```

### 3.2 Dictionary & Set Comprehensions
```python
# Dictionary comprehension
word_lengths = {word: len(word) for word in words}

# Set comprehension
unique_lengths = {len(word) for word in words}

# Dictionary with conditional
filtered_dict = {k: v for k, v in original.items() if v > 10}
```

## 4. Function
### 4.1 Advanced Function Features
```python
# Default arguments
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

# *args and **kwargs
def flexible_func(*args, **kwargs):
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")

# Lambda with multiple arguments
sort_by_second = lambda x: x[1]
data.sort(key=sort_by_second)
```

### 4.2 Decorators (Basic Syntax)
```python
# Simple decorator usage
@property
def full_name(self):
    return f"{self.first} {self.last}"

@staticmethod
def utility_function():
    return "This doesn't need self"
```

## 5. Error Handling
```python
# Try-except with multiple exceptions
try:
    result = risky_operation()
except (ValueError, TypeError) as e:
    print(f"Error occurred: {e}")
except Exception as e:
    print(f"Unexpected error: {e}")
else:
    print("No errors occurred")
finally:
    cleanup()

# Context managers
with open("file.txt", "r") as f:
    content = f.read()
```


## 6. Object-Oriented Programming