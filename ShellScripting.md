
# Bash Shell Scripting Guide

---
1. Create a Script File: Open a terminal and type:
```
gedit hello.sh       # Creates a file named "hello.sh"  
```
2.Add Code:
Type these lines into the file:
```
#!/bin/bash                # Shebang: "Tell Compuetr to Use Bash to run this!"  
echo "Hello, World!"         # Prints "Hello, World!" on the screen  
```

3. Make It Executable: Save the file, then type:
```
chmod +x hello.sh        # Gives permission to run the script   
```
4.Run It: Command to execute the script:
```
./hello.sh 
```
---


## Variables
 We can declare a variable in a bash script using VariableName=Value and can access it using $VariableName.
```bash
name="Alice"
age=18
echo "Hello, $name my age is $age"
```

- No spaces around `=`.
- Quote variables: `"$name"`

---

## Comments

```bash
# This is a comment
```

---

## Control Structures

### If-Else

#### Syntax of If-else statement:

```bash
if [ expression ]; then
    statements
elif [ expression ]; then
    statements
else 
    statements
fi
```
> Example : 
```bash
num=5
if [ $num -gt 3 ]; then
  echo "Greater than 3"
else
  echo "Less or equal to 3"
fi
```

- `-gt` -> greater than
- `-lt` -> less than
- `-ge` -> greater than equal to
- `-le` -> less than equal to
- `eq` -> equal to
- `ne` -> not equal to

---

### For Loop

```bash
for i in 1 2 3; do
  echo "Number $i"
done
```
```bash
for i in {1..5}; do
  echo "Number $i"
done
```

```bash
for ((i=0; i<=10; i++)); do
    echo "Number $i"
done
```

### While Loop

```bash
count=1
while [ $count -le 3 ]; do
  echo "Count $count"
  count=$((count+1))
done
```

### Until Loop

```bash
count=10
until [ $count -ge 0 ]; do
  echo "Count $count"
  count=$((count-1))
done
```

## 6. Reading Input

```bash
echo "Enter your name:"
read username
echo "Your name is $username"
```

```bash
read -p "Enter your name: " username
echo "Your name is $username"
```

---

## Functions

```bash
greet() {
  echo "Hello, $1"
}
greet "Bob"
```

---


## Files and  Directory Validation

```bash
#!/bin/bash

directory="/path/to/directory"  # Change this to your directory path
file="jdoodle.sh"

if [ -d "$directory" ]; then  # Check if directory exists
  if [ -f "$directory/$file" ]; then
    echo "$file exists in $directory."
  else
    echo "$file does not exist in $directory."
  fi
else
  echo "Directory $directory does not exist."
fi
```

- `-d` -> for directory
- `-f` -> for file
---

## Command Line Arguments

### Positional Arguments

- `$0`: Script name
- `$1`, `$2`, ..., `$n`: Arguments
- `$#`: Number of arguments
- `$@`: All arguments

```bash
#!/bin/bash
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
echo "All arguments: $@"
```

### Looping Over Arguments

```
for arg in "$@"; do
  echo "$arg"
done
```

### Default Argument Values

```bash
name=${1:-"Anonymous"}
echo "Hello, $name"
```

---

## Argument Validation

```bash
if [ $# -lt 2 ]; then
  echo "Usage: $0 arg1 arg2"
  exit 1
fi
```

---

## Case 

```bash
#!/bin/bash
read -p "Enter Number: " opt
  case $opt in
    1) echo "Monday";;
    2) echo "Tuesday" ;;
    3) echo "Wednesday" ;;
    4) echo "Thursday";;
    5) echo "Friday";;
    6) echo "Saturday";;
    7) echo "Sunday";;
    *) echo "Invalid";;
  esac
```

---

## Practical Exercise
 To count no. of Lines in some text file.
```bash
#!/bin/bash
echo "Enter filename:"
read fname
if [ -f "$fname" ]; then
  echo "$fname has $(wc -l < "$fname") lines."
else
  echo "File not found."
fi
```
