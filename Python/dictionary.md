# Overview
> It's smiliar to js's **object**

# Tips
## Dictionary to a list ?
```
inputDictionary = {'Hello': 10, 'Tutorialspoint': 20, 'python': 30}
```
### Using keys() Method
```
resultList = list(inputDictionary.keys())
--- Output ---
['Hello', 'Tutorialspoint', 'python']
```
### Using values() Method
```
resultList = list(inputDictionary.values())
--- Output ---
[10, 20, 30]
```
### Using List Comprehension
```
resultList = [(key, value) for key, value in inputDictionary.items()]
--- Output ---
[('Hello', 10), ('Tutorialspoint', 20), ('python', 30)]: 
```
# Reference
- https://www.tutorialspoint.com/python/python_dictionary.htm
- https://www.tutorialspoint.com/How-to-convert-Python-Dictionary-to-a-list
