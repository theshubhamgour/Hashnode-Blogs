---
title: "Day #13: Basics of Python"
datePublished: Mon Nov 20 2023 04:30:41 GMT+0000 (Coordinated Universal Time)
cuid: clp6eseaz000209la3yd68kaa
slug: day-13-basics-of-python
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/D9Zow2REm8U/upload/4d11dc665dffab420e111c3f81dcc74e.jpeg
tags: python, devops

---

## **What is Python?**

* Python is an Open source, general-purpose, high-level, and object-oriented programming language.
    
* It was created by **Guido van Rossum**
    
* Python consists of vast libraries and various frameworks like Django, Tensorflow, Flask, Pandas, Keras etc.
    

**How to Install Python?**

You can install Python in your System whether it is Windows, MacOS, ubuntu, centos etc. Below are the links for the installation:

* [Windows Installation](https://www.python.org/downloads/)
    
* Ubuntu: apt-get install python3.6
    

## Task 1: Install Python in your respective OS, and check the version.

```plaintext
[root@ip-172-31-1-21 ec2-user]# yum install python
[root@ip-172-31-1-21 ec2-user]# python --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700375295639/d0eb647c-4e7c-435b-8430-45213b18424b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700375323302/c4c4dcf7-d5d1-4276-ab22-534ebb7b17a1.png align="center")

## Task 2: Read about different Data Types in Python.

1. **Numeric Data Types:** Python supports several numeric data types, including integers (`int`), floating-point numbers (`float`), and complex numbers (`complex`). Integers represent whole numbers, floats handle decimal numbers, and complex numbers involve both real and imaginary parts.
    
    ```plaintext
    \# Numeric Examples
    integer_number = 42
    float_number = 3.14
    complex_number = 2 + 3j
    ```
    
2. **Sequence Types:** Python provides different sequence types, namely strings (`str`), lists (`list`), and tuples (`tuple`). Strings are used for text, lists are mutable sequences, and tuples are immutable sequences.
    
    ```plaintext
    # Sequence Examples
    text_string = "Hello, Python!"
    number_list = [1, 2, 3, 4, 5]
    immutable_tuple = (10, 20, 30)
    ```
    
3. **Boolean Type:** The Boolean data type (`bool`) is used to represent truth values, either `True` or `False`. Booleans are fundamental for conditional statements and logical operations.
    
    ```plaintext
    # Boolean Example
    is_python_fun = True
    ```
    
4. **Set Types:** Python supports sets (`set`), an unordered collection of unique elements. Sets are useful for mathematical operations like union, intersection, and difference.
    
    ```plaintext
    # Set Example
    unique_numbers = {1, 2, 3, 4, 5}
    ```
    
5. **Mapping Type:** Dictionaries (`dict`) are used to store key-value pairs, providing a mapping between keys and values. They are mutable and versatile for various data manipulation tasks.
    
    ```plaintext
    # Dictionary Example
    student_info = {'name': 'Alice', 'age': 25, 'grade': 'A'}
    ```
    
6. **None Type:** The `None` type represents the absence of a value or a null value. It is commonly used to initialize variables or as a placeholder.
    
    ```plaintext
    # None Example
    empty_variable = None
    ```
    
7. **Special Types:** In addition to the common data types mentioned above, Python has several special types like `bytes`, `bytearray`, and `memoryview` for handling binary data and memory views.
    
    ```plaintext
    # Special Types Example
    byte_data = b'BinaryData'
    ```
    

##   
Conclusion:

In conclusion, a solid understanding of Python's diverse set of data types is fundamental for any programmer aiming to harness the full power of the language. Python's versatility lies not only in its readability and simplicity but also in its ability to handle various data structures seamlessly.