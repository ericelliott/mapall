
```js
const promises = [
  new Promise((x, reject) => setTimeout(() => reject(new Error('10'), 10))),
  new Promise((resolve) => setTimeout(() => resolve('20'), 20)),
  new Promise((x, reject) => setTimeout(() => reject(new Error('20'), 20)))
];

mapAll(promises).then(res => console.log(res));
// [
//    {"status":"rejected","error":{}},
//    {"status":"resolved","val":"20"},
//    {"status":"rejected","error":{}}
// ]
```

```js
const promises = [];

mapAll(promises).then(res => console.log(res)); // []
```
