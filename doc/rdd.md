`Promise.all()` is great, but as soon as any promise is rejected, the returned promise rejects.

For unit testing, we sometimes want to inspect the resolved / rejected status of every promise in an array.

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

If you pass an empty array, it immediately resolves to an empty array:

```js
const promises = [];

mapAll(promises).then(res => console.log(res)); // []
```
