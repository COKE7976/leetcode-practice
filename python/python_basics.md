# Math
```python
import math

print(-123 % 10)            # 7
print(math.fmod(-123, 10))  # -3

print(math.gcd(8, 12))      # 4, highest common factor
print(math.lcm(8, 12))      # 24, least common multiple
```
```python
print(10 / 2)               # 5.0
print(int(10 / 2))          # 5
print(10 // 2)              # 5
```
```python
print(2 ** 2)               # 4
```
```python
print(math.floor(3.14))     # 3
print(math.floor(-3.14))    # -4

print(math.ceil(3.14))     # 4
print(math.ceil(-3.14))    # -3
```

# List
```python
nums[0]              # First element
nums[-1]             # Last element
nums[-2]             # Last second element
```
```python
# list[start : stop : step], start defaults to the end when be None, stop defaults to the beginning when be None
nums = [0, 1, 2, 3, 4]
nums[1:3]            # [1, 2]
nums[::-1]           # Reversed list
```
```python
nums.append(5)       # Add to end
nums.insert(2, 99)   # Insert 99 at index 2
```
```python
nums.pop()           # Remove last element and return it
nums.pop(1)          # Remove element at index 1
nums.remove(3)       # Remove the first occurrence of value 3
```
```python
min(nums)
max(nums)
sum(nums)
```
```python
num = [1, 2, 3]
num_copy = num[::]

print(num_copy)               # [1, 2, 3]
print(num_copy == num)        # True  (same values)
print(num_copy is num)        # False (different objects)
```
```python
# Use deepcopy() to Fully Duplicate Nested Structures
import copy

original = [[1, 2], [3, 4]]
deep = copy.deepcopy(original)

deep[0][0] = 999

print("Original:", original)  # [[1, 2], [3, 4]]
print("Deep:", deep)          # [[999, 2], [3, 4]]
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
words = ['I', 'love', 'Python']
sentence = ' '.join(words)  # "I love Python"
```
```python
nums = [1, 2, 3]
string = "".join(str(n) for n in nums)
print(string)  # "123"
```
```python
line = "apple,banana,grape"
fruits = line.split(",")  # ['apple', 'banana', 'grape']
```
```python
s = "abc123"
s.isalpha()  # False, "a - z" or "A - Z" only
s.isdigit()  # False, "0 - 9" only
s.isalnum()  # True
```
```python
s = "a-b-c"
s.replace("-", "")  # "abc"
```
```python
s = "banana"
s.count("a")        # 3
```
```python
s = "aBc"
print(s.lower())    # abc
print(s.upper())    # ABC
```

# Set
```python
myset = set()
or
myset = {1, 2, 3}

myset.add(4)         # {1, 2, 3, 4}
myset.remove(2)      # Removes 2, error if not found
myset.discard(99)    # No error if 99 not in set

if 3 in myset:
    print("Found!")  # Found!
```
```python
nums = [1, 2, 2, 3, 3]
unique = set(nums)   # {1, 2, 3}
```
```python
a = {1, 2, 3}
b = {3, 4, 5}

a & b  # Intersection → {3}
a | b  # Union        → {1, 2, 3, 4, 5}
a - b  # Difference   → {1, 2}
```

# HashMap
```python
mp = {}
or
mp = {'a': 1, 'b': 2}

print(mp.keys())            # ['a', 'b']
print(mp.values())          # [1, 2]
print(mp.items())           # [(a, 1), (b, 2)]
```
```python
mp = {}
mp["apple"] = 5
mp["apple"] += 1
print(mp["apple"])          # 6
print(mp["banana"])         # KeyError if not exists
print(mp.get("banana", 0))  # returns 0 if key doesn't exist

mp.pop("apple", None)       # returns None if key doesn't exist, otherwise returns the value of key "apple"

if "apple" in mp:
    print("Yes")            # Yes

for key in mp:
    print(key, mp[key])     # print out all the values

for key, value in mp.items():
    print(key, value)       # print out all the key - value pairs
```
```python
mp = defaultdict(int)       # gives default value when key not exists, default value can be a set, a list, ...
print(mp["new_key"])        # 0
mp.pop("not_seen", 0)       # returns 0, as dict.pop(), a defautlt value is needed when performing pop() in case the key does not exist
```
```python
from collections import Counter

nums = [1, 1, 2, 3, 3, 3]
count = Counter(nums)
print(count[1])             # 2
print(count[2])             # 1
print(count[3])             # 3
```

# Heap
```python
min_heap = [3, 1, 4, 1, 5]
heapq.heapify(min_heap)             # time complexity = O(n)
print(min_heap)                     # [1, 1, 4, 3, 5], internally rearranged as a min heap
print(min_heap[0])                  # 1, the smallest

heapq.heappush(min_heap, 3)         # push 3 into the min heap
smallest = heapq.heappop(min_heap)  # removes and returns smallest
print(smallest)                     # 1
```
```python
arr = [7, 10, 4, 3, 20, 15]
print(heapq.nsmallest(3, arr))      # [3, 4, 7]
print(heapq.nlargest(3, arr))       # [20, 15, 10]
```
```python
# build a max heap
max_heap = []
heapq.heappush(max_heap, -3)
heapq.heappush(max_heap, -1)
heapq.heappush(max_heap, -2)

print(-heapq.heappop(max_heap))     # 3
```
```python
# heap sort, time complexity O(nlogn)
arr = [3, 1, 4, 1, 5]
heapq.heapify(arr)
sorted_arr = [heapq.heappop(arr) for _ in range(len(arr))]
print(sorted_arr)                   # [1, 1, 3, 4, 5]
```

# Double Ended Queue
```python
from collections import deque
dq = deque()                 # empty
or
dq = deque([1, 2, 3])        # from iterable

dq.append(4)                 # add to right: [1, 2, 3, 4]
dq.appendleft(0)             # add to left:  [0, 1, 2, 3, 4]

dq.pop()                     # remove from right, returns last element
dq.popleft()                 # remove from left, returns first element

left = dq[0]                 # first element
right = dq[-1]               # last element
```
```python
dq.rotate(2)                 # move last 2 elements to the front, [1, 2, 3, 4, 5] --> [4, 5, 1, 2, 3]
dq.rotate(-1)                # move first element to the end, [1, 2, 3, 4, 5] --> [2, 3, 4, 5, 1]
```
```python
dq.remove(3)                 # removes first matching element
```
```python
# fixed size (old items removed automatically)
dq = deque(maxlen=3)
dq.extend([1, 2, 3])         # add multiple to right
dq.append(4)                 # deque now [2, 3, 4] (1 was dropped automatically)
```

# any & all
```python
any([0, False, 5])             # True  (because 5 is truthy)
any([0, False, None])          # False (no truthy values)

nums = [1, 2, 3]
any(n > 2 for n in nums)       # True
```
```python
all([1, "hello", [1]])         # True (all truthy)
all([1, "", 3])                # False ("" is falsy)

nums = [2, 4, 6]
all(n % 2 == 0 for n in nums)  # True
```
```python
any([])                        # False
all([])                        # True, vacuously true
```
