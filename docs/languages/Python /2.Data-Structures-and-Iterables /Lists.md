# Lists

Lists in Python are widely used to store a collection of elements in a single variable. Lists are mutable, can hold any data type, and accept repeat values. Each element in a list is called an item. Items can be added, removed, or edited.

## Initializing lists
Lists are created using square brackets, with each element in the list separated by a comma. You can create a list with zero or more items. A list with zero items is like a placeholder for values to be added later. For example, imagine that you are a student and you want to track your test scores for a class. You can start by initializing an empty list, so that you can add your scores as you complete your tests. 

The following code shows how to create an empty list named test_scores.

```
test_scores = []
```

The following example shows a list named test_scores that holds five numeric values.

```
test_scores = [93, 87, 90, 85, 86]
```

## Accessing items in a list

Lists are ordered, which means that each item in the list has a designated position. You can access each item based on its position. The positional reference can be counted from the beginning of the list (positive index) or the end of the list (negative index). Counting from left to right, the index starts at 0 and counts up consecutively.

To refer to the last element of a list or to refer to an item based on its position from the end, you can use the negative index. The last item in a list has an index of -1, and preceding items count down consecutively moving from right to left. This means that the second-to-last item has an index of -2. You use -3 to refer to the third-to-last item on the list, and so on. 

For the list in the following image, the 0 index refers to the same item as the -5 index.

<img width="938" alt="1" src="https://github.com/user-attachments/assets/faddcc28-fcb7-4f98-8453-3966af56b2d4" />






