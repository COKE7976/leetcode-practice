# Math
```python
print(-123 % 10)            # 7
print(math.fmod(-123, 10))  # -3
```
```python
print(10 / 2)   # 5.0
print(10 // 2)  # 5
```
```python
print(2 ** 2)  # 4
```

# List
```python
nums[0]   # First element
nums[-1]  # Last element
nums[-2]  # Last second element
```
```python
# list[start : stop : step], start defaults to the end when be None, stop defaults to the beginning when be None
nums[1:3]    # [index_2, index_3]
nums[::-1]   # Reversed list
```
```python
nums.append(5)      # Add to end
nums.insert(2, 99)  # Insert 99 at index 2
```
```python
nums.pop()      # Remove last element and return it
nums.pop(1)     # Remove element at index 1
nums.remove(3)  # Remove the first occurrence of value 3
```
```python
min(nums)
max(nums)
sum(nums)
```
```python
num = [1, 2, 3]
num_copy = num[::]

print(num_copy)         # [1, 2, 3]
print(num_copy == num)  # True  (same values)
print(num_copy is num)  # False (different objects)
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
# String
```python
nums = [1, 2, 3]
string = "".join(str(n) for n in nums)
print(string) # "123"
```
