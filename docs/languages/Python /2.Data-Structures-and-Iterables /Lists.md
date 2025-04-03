# Lists

Lists in Python are widely used to store a collection of elements in a single variable. Lists are mutable, can hold any data type, and accept repeat values. Each element in a list is called an item. Items can be added, removed, or edited.

## Initializing lists
Lists are created using square brackets, with each element in the list separated by a comma. You can create a list with zero or more items. A list with zero items is like a placeholder for values to be added later. For example, imagine that you are a student and you want to track your test scores for a class. You can start by initializing an empty list, so that you can add your scores as you complete your tests. 

The following code shows how to create an empty list named test_scores.

```python
test_scores = []
```

The following example shows a list named test_scores that holds five numeric values.

```python
test_scores = [93, 87, 90, 85, 86]
```

## Accessing items in a list

Lists are ordered, which means that each item in the list has a designated position. You can access each item based on its position. The positional reference can be counted from the beginning of the list (positive index) or the end of the list (negative index). Counting from left to right, the index starts at 0 and counts up consecutively.

To refer to the last element of a list or to refer to an item based on its position from the end, you can use the negative index. The last item in a list has an index of -1, and preceding items count down consecutively moving from right to left. This means that the second-to-last item has an index of -2. You use -3 to refer to the third-to-last item on the list, and so on. 

For the list in the following image, the 0 index refers to the same item as the -5 index.

<img width="938" alt="1" src="https://github.com/user-attachments/assets/faddcc28-fcb7-4f98-8453-3966af56b2d4" />

You can access a single element using the list name, square brackets, and the index number. You can also access a range of elements by specifying, in brackets, where to start and end the list. This is called slicing. Slicing lets you extract a portion of a sequence, like a list. The syntax is as follows:

> sequence[start:end]

Here are a couple of important points regarding slicing:
- Indexing starts at 0.
- The end index is not included in the slice.
- If you omit the start, it defaults to the beginning of the sequence.
- If you omit the end, it goes to the end of the sequence.

You might recall string slicing from a previous module. Slicing items in a list works fundamentally the same way slicing a string does. The following is an example of slicing on a list named fruits:

```python
fruits = ["apple", "banana", "cherry", "date", "elderberry"]

print(fruits[1:4])  # Output: ["banana", "cherry", "date"]
print(fruits[:3])   # Output: ["apple", "banana", "cherry"]
print(fruits[2:])   # Output: ["cherry", "date", "elderberry"]
```
Slicing is useful for working with parts of your data without changing the original sequence. It allows you to be able to focus on just the part of your data that you need at any given moment.

The following code example creates a list called my_list and uses slicing to print specific items from that list to the console. You can use the Copy code button to copy the code into your practice environment. Run the file and review the output.

```python
my_list = ["first", "second", "third", "fourth"]

# print single element using the positive index

print(my_list[1])

# print single element using the negative index

print(my_list[-1])

# print range of values using the slice operator

print(my_list[1:3])
```

*Expected output:*
```plaintext
second
fourth
["second", "third"]
```





