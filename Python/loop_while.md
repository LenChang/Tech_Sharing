# While
```
i = 0
while i < 5:
    i += 1
    if i == 3:
        continue
    print(i)
    if i == 4:
        break;
else:
    print("i is larger / equal to 5")
```

# Loop
> *enumerate* and *zip* are the best way for you to use it

```
presidents = ["Washington", "Adams", "Jefferson", "Madison", "Monroe", "Adams", "Jackson"]
for idx, name in enumerate(presidents):
    print(f"President {idx}, {name}")
```

```
colors = ["red", "green", "blue", "purple"]
ratios = [0.2, 0.3, 0.1, 0.4]
for color, ratio in zip(colors, ratios):
    print("{}% {}".format(ratio * 100, color))
```

# Reference
- https://treyhunner.com/2016/04/how-to-loop-with-indexes-in-python/
