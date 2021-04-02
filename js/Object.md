# Object.create()、 new Object() 和 {} 的区别

```js

const obj = {a: 3};
console.log(Object.getOwnPropertyDescriptor(obj, 'a')); // {value: 3, writable: true, enumerable: true, configurable: true}

const obj1 = new Object({a: 1});
console.log(Object.getOwnPropertyDescriptor(obj1, 'a')); // {value: 3, writable: true, enumerable: true, configurable: true}

const obj2 = Object.create(null);
console.log(obj1.__proto__); // undefined

const obj3 = Object.create({}, {
  a: {
    value: 3,
    configurable: false,
  }
});

console.log(obj3.__proto__.a); // 3。 在原型链上赋值属性内容。

```

## 思考
  * 在非必要的情况下，是否只需要用字面量方式生成对象。 

## 参考
  * <a href="https://blog.csdn.net/qq_39207948/article/details/81204411">Object.create()和new object()和{}的区别</a>


# obj.a = 3 、 Object.defineProperty 的区别

```js

const obj = {};
obj.a = 3;
console.log(Object.getOwnPropertyDescriptor(obj)); // {value: 3, writable: true, enumerable: true, configurable: true}

const obj1 = {};
Object.defineProperty(obj1, {value: 3}); // 默认属性不同  {value: 3, writable: false, enumerable: false, configurable: false}

```