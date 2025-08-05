# Math
`math.fmod(-123, 10) = -3`, but `-123 % 10 = 7`  
`/`, division always gives float output, so one can use `int(x / 10)` or `x // 10`  

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
