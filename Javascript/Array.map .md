# Get Started
- Collecting interesting use cases
# Use Case
## implement Array.map with async. way
### Sync. way
```
const arr = [1, 2, 3];

const syncRes = arr.map((i) => {
 return i + 1;
});

console.log(syncRes);
// 2,3,4
```

### Async. way
```
const arr = [1, 2, 3];
const sleep = (delay) => new Promise((resolve) => setTimeout(resolve, delay))

const asyncRes = await Promise.all(arr.map(async (i) => {
 await sleep(10);
 return i + 1;
}));

console.log(asyncRes);
// 2,3,4
```
## Read files concurrency
### Sync. way
```
async function printFiles () {
  const files = await getFilePaths();

  for (const file of files) {
    const contents = await fs.readFile(file, 'utf8');
    console.log(contents);
  }
}
```
### Async. way
```
async function printFiles () {
  const files = await getFilePaths();

  await Promise.all(files.map(async (file) => {
    const contents = await fs.readFile(file, 'utf8')
    console.log(contents)
  }));
}
```


# Reference
- https://zhuanlan.zhihu.com/p/134239237
- https://builtin.com/software-engineering-perspectives/javascript-sleep
- https://stackoverflow.com/questions/37576685/using-async-await-with-a-foreach-loop
