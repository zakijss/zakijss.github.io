---
title: "Automating IP Removal from an Allow List Using Python"
date: 2025-05-24
categories: [Portfolio, Python]
tags: [file-handling, python, automation, scripting, security+, project, portfolio,]
description: A Python script that opens a file, reads and parses a list of IP addresses, removes unauthorized entries, and rewrites the cleaned list.
toc: true
comments: false
media_subpath: /assets/img/
---

## Project Description

As a simulated exercise, access to restricted content is controlled using an allow list of IP addresses stored in a file named `allow_list.txt`. A separate list, `remove_list`, contains IPs that should no longer have access to those systems. I created a Python algorithm that automates the process of removing these disallowed IPs from the allow list. This kind of automation reduces the risk of human error and supports stronger access control in sensitive environments like healthcare.

---

## Opening the File That Contains the Allow List

To begin the process, I assigned the name of the file to a variable and opened it using Python's `with` statement:

````python
import_file = "allow_list.txt"
with open(import_file, "r") as file:
    ip_addresses = file.read()
````
![Screenshot showing code](reading-contents.png){: w="700" h="400" }
_Overview of the Python file code._

The `open()` function is used here in read mode (`"r"`) to access the file’s contents. The `with` statement ensures the file is automatically closed once we finish reading it, helping prevent resource leaks. Within the `with` block, I used the `.read()` method to read the full contents of the file and stored it in the variable `ip_addresses`.

-

## Read and Convert the Contents

Once I had the file contents as a string, I needed to convert it into a more manageable format, a list. This was done using the `.split()` method:

````python
ip_addresses = ip_addresses.split("\n")
````
![Screenshot showing code of the content split](string-conversion.png){: w="700" h="400" }
_Overview of the Python file code._

The `.split("\n")` call separates each line of the string into a list element. This structure makes it easier to search, filter, and remove specific IP addresses.

---

## Iterate Through the Remove List

Next, I defined a list of IPs that should be removed and set up a `for` loop to check each one:

![Screenshot showing code of the IP remove_list](remove-list.png){: w="700" h="400" }
_Overview of the Python file code._

```python
remove_list = ["10.0.0.5", "172.16.0.3"]
for element in remove_list:
    if element in ip_addresses:
        ip_addresses.remove(element)
```
![Screenshot showing code](removing-ip.png){: w="700" h="400" }
_Overview of the Python file code._


Here, the `for` loop processes each entry in `remove_list`. For each `element`, I first checked if it was present in `ip_addresses` using a conditional. If it was, I used the `.remove()` method to delete it. This works efficiently in this scenario since the IP list has no duplicates.

---

## Update the File with the Revised List

After removing the disallowed IPs, I converted the updated list back into a string using `.join()`, with newline characters to preserve the file’s format:

```python
ip_addresses = "\n".join(ip_addresses)
```


Then, I opened the file again in write mode (`"w"`) and used `.write()` to overwrite its contents with the updated list:

```python
with open(import_file, "w") as file:
    file.write(ip_addresses)
```

![Screenshot showing code of the IP overwrite](updating-ip.png){: w="700" h="400" }
_Overview of the Python file code._

Using `"w"` tells Python to replace the contents of the file. This ensures that the file now reflects the new state of authorized IP addresses: with all disallowed entries removed.

---

## Concepts and Skills Demonstrated

* Using `with open()` to safely handle files
* Reading file content with `.read()` and parsing it with `.split()`
* Iterating through a list and applying conditional logic
* Removing list elements with `.remove()`
* Writing data back to a file using `.write()` and `.join()`

These are essential techniques for automating tasks in cybersecurity, especially for managing logs, access lists, and audit records.

---

## Summary

I developed a Python-based solution to remove disallowed IP addresses from an access control list maintained in a text file. The process involved opening the file, reading its contents, converting the string of IP addresses into a list, and then checking that list against a predefined set of IPs to be removed. After filtering out any matches, I converted the list back into a properly formatted string and overwrote the original file. This task not only reflects real-world cybersecurity challenges but also demonstrates my ability to automate repetitive tasks using fundamental Python programming skills.

---
