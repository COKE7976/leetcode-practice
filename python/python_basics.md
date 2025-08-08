# Math
```python
print(-123 % 10)           # 7
print(math.fmod(-123, 10)  # -3
```
```python
print(10 / 2)   # 5.0
print(10 // 2)  # 5
```
```python
print(2 ** 2)  # 4
```

# List
`list[start:stop:step]`  
`reverse_list = list[::-1]`  
- start = `None`, defaults to the end of the list  
- stop = `None`, defaults to the beginning of the list

`list.append(val)` appends `val` at the end  
`list.insert(0, val)` inserts `val` at the start  
  
`list.remove(val)` removes the first occurrence of `val`  
`list.pop(index)` pops out the element at index `index`, `list.pop()` pops out the last element  

`del arr[1]` removes element at index 1  
`del arr[1:3]` removes a slice (elements at index 1 & 2)  

# String
```python
nums = [1, 2, 3]
string = "".join(str(n) for n in nums)
print(string) # "123"
```
# Sort
```python
nums = [3, 1, 4, 2]

# In-place sorting (modifies original list)
nums.sort()
print(nums)  # [1, 2, 3, 4]

# Reversed order
nums.sort(reverse=True)
print(nums)  # [4, 3, 2, 1]
```
```python
nums = [5, 2, 8, 1]

sorted_nums = sorted(nums)
print(sorted_nums)  # [1, 2, 5, 8]
print(nums)         # [5, 2, 8, 1] — original is unchanged
```
```python
words = ["banana", "apple", "cherry"]
words.sort()
print(words)  # ['apple', 'banana', 'cherry']
```
```python
words = ["banana", "kiwi", "apple", "fig"]

# Sort by length of each word
words.sort(key=len)
print(words)  # ['fig', 'kiwi', 'apple', 'banana']
```
```python
intervals = [(1, 3), (2, 5), (0, 4)]

# Sort by the second item in each tuple (end time)
intervals.sort(key=lambda x: x[1])
print(intervals)  # [(1, 3), (0, 4), (2, 5)]
```
```python
my_dict = {'a': 3, 'b': 1, 'c': 2}

# Convert to list of tuples and sort by value
sorted_items = sorted(my_dict.items(), key=lambda x: x[1])
print(sorted_items)  # [('b', 1), ('c', 2), ('a', 3)]
```
