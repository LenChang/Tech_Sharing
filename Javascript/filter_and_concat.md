###### tags: coding
# Conbine filter and push
## Question
I wanna to filter an array and push a new one into it. How do i write it as FP approach ?

### Something is wrong...
```
...
oldArr
    .filter((x) => x.type !== 'label')
    .push(
        [{
            class: 'tmpAAA',
            type: 'label',
            x: 11,
            y: 11,
            height: 22,
            width: 22,
        },]);
...
```

### Soution 1
```
...
const newArr = oldArr
    .filter((x) => x.type !== 'label')
    .concat(
        [{
            class: 'tmpAAA',
            type: 'label',
            x: 11,
            y: 11,
            height: 22,
            width: 22,
        },]);
...
```
