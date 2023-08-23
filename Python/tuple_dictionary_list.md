# Overview
| List               | Tuple                    | Dictionary  |
| --- |---|---|
| [...]              | (...)                    | {...} |
| Lists are mutable. | Tuple are **immutable**  | Dictionary are mutable |
| Lists are ordered. | Tuple are **unordered**  | Dictionary are ordered |
| array of js        | array of js              | object of js |

# Tips
### Dict to List
```
resultList = list(inputDictionary.keys())
--- Output ---
['Hello', 'Tutorialspoint', 'python']
```
```
resultList = list(inputDictionary.values())
--- Output ---
[10, 20, 30]
```
```
resultList = [(key, value) for key, value in inputDictionary.items()]
--- Output ---
[('Hello', 10), ('Tutorialspoint', 20), ('python', 30)]: 
```
# Reference
- https://www.tutorialspoint.com/List-vs-tuple-vs-dictionary-in-Python
- https://www.tutorialspoint.com/python/python_dictionary.htm
- https://www.tutorialspoint.com/How-to-convert-Python-Dictionary-to-a-list
