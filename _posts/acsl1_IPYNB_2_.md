---

---

```python
def findDiscardSum(originalRows, tiles):
    list = []
    discard = 0
    tiles = tiles.split()
    originalRows = str(originalRows)
    for i in range(len(originalRows)):
        list.append(originalRows[i])
    for i in range(len(tiles)):
        for i in range(len(list)):
            if (tiles[i] == list[i] + tiles[i][0]):
                list[i] = list[i] + tiles[i][0]
            elif (tiles[i] == tiles[i][0] + list[i]):
                list[i] = tiles[i][0] + list[i]
            else:
                discard = discard + int(tiles[i][0]) + int(tiles[i][1])
                print("addition 1 ",int(tiles[i][0]))
                print("addition 2 ",int(tiles[i][1]))
    return discard

blah = "56 27 73 34 99 45 32 19 64 57 18"
print(findDiscardSum(5923, blah))
```

    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    addition 1  5
    addition 2  6
    addition 1  2
    addition 2  7
    addition 1  7
    addition 2  3
    addition 1  3
    addition 2  4
    407



```python
list = ["100", "200", "300"]
hello = list[0][1]

print(hello)
```

    0



```python
a = ["41","42","21"]
b = ["4","4","1"]

def hello(list, tiles):
    for i in range(len(list)):
        if (tiles[i] == list[i] + tiles[i][:1]):
            list[i] = list[i] + tiles[i][:1]
    return list

print(hello(b, a))
```

    ['4', '4', '1']



```python
def findDiscardSum(originalRows, tiles):
    list = []
    discard = 0
    tiles = tiles.split()
    originalRows = str(originalRows)
    for i in range(len(originalRows)):
        list.append(originalRows[i])
    for i in range(len(tiles)):
        for i in range(len(list)):
            if (tiles[i] == list[i] + tiles[i][1]):
                list[i] = list[i] + tiles[i][1]
            elif (tiles[i][::-1] == tiles[i][0] + list[i]):
                list[i] = tiles[i][0] + list[i]
            else:
                discard = discard + int(tiles[i][0]) + int(tiles[i][1])
    return discard

blah = "56 27 73 34 99 45 32 19 64 57 18"
print(findDiscardSum(5923, blah))
```

    389



```python
hi = "10 20 30 40 50"
yolo = hi.split()
yolo.append(85)
print(yolo)
```

    ['10', '20', '30', '40', '50', 85]



```python
tiles = "56 27 73 34 99 45 32 19 64 57 18"
list = []
for number in tiles:
    while tiles[number] != " ":
        list.append(number)
print(list)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    /tmp/ipykernel_953/1818766058.py in <module>
          2 list = []
          3 for number in tiles:
    ----> 4     while tiles[number] != " ":
          5         list.append(number)
          6 print(list)


    TypeError: string indices must be integers



```python
def findDiscardSum(originalRows, tiles):
    list = []
    discard = 0
    tiles = tiles.split()
    originalRows = str(originalRows)
    for i in range(len(originalRows)):
        list.append(originalRows[i])
    for i in range(len(tiles)):
        for n in range(len(list)):
            if tiles[i][0] == list[n]:
                list[n] += tiles[i][1]
            elif tiles[i][1] == list[n]:
                list[n] += tiles[i][0]
            else:
                discard =  discard + int(tiles[i][0]) + int(tiles[i][1])
    return discard

print(findDiscardSum(5923, "56 27 73 34 99 45 32 19 64 57 18"))
```

    392

