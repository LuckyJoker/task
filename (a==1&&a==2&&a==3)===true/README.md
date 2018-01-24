# JavaScript: Can (a==1 && a==2 && a==3) ever evaluate to true?

## Yes, it can. Understand how in this article!

Recently, an interesting code snippet has been making the rounds on [Twitter]

- **The question is **— Can `(a==1 && a==2 && a==3)` ever evaluate to true?
- **The answer is **— Yes.

In this article we’ll examine this code and why it works:

```
const a = {
  num: 0,
  valueOf: function() {
    return this.num += 1
  }
};
```

```
const equality = (a==1 && a==2 && a==3);
```

```
console.log(equality); // true
```

If you’re using Google Chrome, open up your developer console with [*windows*]: **Ctrl + Shift + J** [*mac*]: **Cmd + Opt + J**

------

### What’s the trick?

There really isn’t one. This code simply takes advantage of two basic JavaScript concepts:

- Loose Equality
- An object’s `valueOf()` function

#### **Loose Equality**

Notice that the equation we’re testing: `(a==1 && a==2 && a==3)`, uses loose equality. This means type coercion will be preformed and we can be a little less precise than we need to be. Since I’ve already done numerous articles on loose equality, I wont go into it here. If you need a refresher on loose quality, read my previous article: [**JavaScript — Double Equals vs. Triple Equals**](https://codeburst.io/javascript-double-equals-vs-triple-equals-61d4ce5a121a)**.**

#### valueOf

JavaScript provides a built in method to convert an object into a primitive value: `Object.prototype.valueOf()`. By default this method returns the object it is being called on.

Lets create an object:

```
const a = {
  num: 0
}
```

As explained above, when we call `valueOf()` on our `a` object, it simply returns the object:

```
a.valueOf();
```

```
// {num: 0}
```

Cool! We can also use `typeof` to verify an object is being returned:

```
typeof a.valueOf();
```

```
// "object"
```

But the real fun with `valueOf()` is that we can overwrite it in order to convert an object into a primitive value. In other words, we can use `valueOf` to return a string, number, boolean, etc. instead of an object. Take a look at the code below:

```
a.valueOf = function() {
  return this.num;
}
```

What we’ve done is overwritten the native code within `valueOf()` for the `a` object. `valueOf()` will now return the value of `a.num` when it is called.

This means if we now call the function:

```
a.valueOf();
```

```
// 0
```

We get `0`! Which makes sense as `0` is the value assigned to `a.num`. We can verify this by running a few tests:

```
typeof a.valueOf();
```

```
// "number"
```

```
a.num == a.valueOf()
```

```
// true
```

Awesome! **But why is this important?**

It’s important because when you check loose equality with two different *types* of operators, JavaScript will attempt to perform type coercion — it will attempt to coerce (convert) the operands into a like/similar type.

In our equation: `(a==1 && a==2 && a==3)`, JavaScript will attempt to coerce the object `a` into a number prior to comparing them. **When performing type coercion on an object, JavaScript first attempts to call the **`valueOf()`** method.**

Since we’ve altered our `valueOf()` method above to return `a.num` which is a number, we can now do the following:

```
a == 0
```

```
// true
```

Holy crap we’ve done it.

**Almost.**

We now need a way to systematically increase the value of `a` every time it is called. Luckily, in JavaScript we have the *Addition Assignment Operator *(`+=`).

The *Addition Assignment Operator* simply adds the value of the right operand to the left variable and assigns the variable with that value. Here’s a simple example:

```
let b = 1
```

```
console.log(b+=1); // 2
console.log(b+=1); // 3
console.log(b+=1); // 4
```

As you can see, every time we use the *Addition Assignment Operator, *the value of our variable increases! Lets apply this same concept to our `valueOf()` function:

```
a.valueOf = function() {
  return this.num += 1;
}
```

Instead of just returning `this.num`, we’re now going to return the value of `this.num` plus `1`, each time it is called.

With this change made, we can finally run our code:

```
const equality = (a==1 && a==2 && a==3);
```

```
console.log(equality); // true
```

It works!

Remember. With loose equality, JS attempts to coerce type. Our object calls `valueOf()` which will return `a.num += 1`, in other words, it returns `a.num` incrementing by `1` each time it is called. From here we’re simply comparing two numbers which results in a `true`. Here’s a breakdown if that helps:

```
a                     == 1   -> 
a.valueOf()           == 1   -> 
a.num += 1            == 1   -> 
0     += 1            == 1   ->
1                     == 1   -> true
a                     == 2   -> 
a.valueOf()           == 2   -> 
a.num += 1            == 2   -> 
1     += 1            == 2   ->
2                     == 2   -> true
a                     == 3   -> 
a.valueOf()           == 3   -> 
a.num += 1            == 3   -> 
2     += 1            == 3   ->
3                     == 3   -> true
```