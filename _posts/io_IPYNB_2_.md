---

---

```python
# Import the sys module to use stdin/stdout
import sys

# sys.stdin/stdout is similar to a file in that we read lines for input/output
my_str = sys.stdin.readline()
sys.stdout.write(str(myStr) + "\n")
# Renaming the read/write methods for convenience
input = sys.stdin.readline
print = sys.stdout.write

# Taking an integer as input
my_int = int(input())
# sys.stdout.write requires you to format code manually
print(str(my_int) + "\n")

"""
For larger inputs, you can buffer the problem's input,
and sort through it yourself. This is the fastest input method for python.
"""
all_data = sys.stdin.read().split("\n")
```


```python
import sys

# Read in a series of numbers on one line into a list
nums = [int(x) for x in input().split()]
# This does the same thing
nums = list(map(int, input().split()))

# stdin/stdout, just replace input() with sys.stdin.readline()
nums = list(map(int, sys.stdin.readline().split()))
```


```python
import sys

# Read in integers n and m on the same line with a list comprehension
n, m = [int(x) for x in input().split()]
# Do the same thing but with map instead
n, m = map(int, input().split())

# stdin and stdout
n, m = map(int, sys.stdin.readline().split())
```


```python
import sys

a, b, c = map(int, input().split())
print("The sum of these three numbers is", a + b + c)

# stdin and stdout
a, b, c = map(int, sys.stdin.readline().split())
print("The sum of these three numbers is", a + b + c)
```


```python
import sys

sys.stdin = open("problemname.in", "r")
sys.stdout = open("problemname.out", "w")
```


```python
"""
Note: The second argument can be omitted in the open()
command for read-only files
"""
fin = open("problemname.in", "r")
fout = open("problemname.out", "w")

# One way to read the file using .readline()
line1 = fin.readline()
# readline() will pick up where you left off
line2 = fin.readline()
line3 = fin.readline()

# Another way is to use a for loop and .readlines()
line_list = []
for line in fin.readlines():
	pass  # Process input here

# printing line_list would give [line1, line2, line3]

# Output:
fout.write(output_text)  # Write to the output file

# f-strings:
variable1 = 1
variable2 = 2
example_str = f"Hello {variable1} {variable2} World!"
# Printing example_str would give Hello 1 2 World!
```


```python
nums = [int(x) for x in input().split()]
n = nums[0]
s = nums[1]
k = 1
count = 0
l = []
for i in range(n):
    h = list(map(int, input().split()))
    l.append(h)
while 0 <= s <= n:
    jp = l[s][0]
    print("lol",jp)
    v = l[s][1]
    print("guh",v)
    if jp == 0:
        k = -(k + v)
        s += k
    elif jp == 1:
        if k >= v:
            count += 1
            s += k
            jp.pop()
        else:
            s += k
    print("count",count)
    
```
