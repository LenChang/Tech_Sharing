# Overview
| List               | Tuple                    | Set      | Dictionary  |
| --- |---|---|---|
| [...]              | (...)                    | {...}    | {[key]: value} |
| Lists are mutable. | Tuple are **immutable**  | Set **won't** allow duplicate elements  | Dictionary are mutable |
| Lists are ordered. | Tuple are ordered  | Set are **unordered**                   | Dictionary are unordered |
| array of js        | array of js              | [... new Set([...])] of js              | object of js |

# Dictionary
| Python | JS |
| --- | ---|
| obj_dic.**get**("key1") | obj_dic["key1"] or obj_dic.key1
| **len**(obj_dic) | Object.keys(obj_dic).length
| obj_dic.**pop**("key1") | delete obj_dic.key1
| **del** obj_dic | obj_dic = undefined

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
