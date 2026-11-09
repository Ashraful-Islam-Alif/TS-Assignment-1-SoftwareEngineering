Type Narrowing in TypeScript

Question: What is Type Narrowing in TypeScript? Provide practical examples using typeof, instanceof, and the in operator.

Introduction

Sometimes a value can be more than one type, for example string | number. TypeScript does not allow us to use a method that belongs to only one of those types. Type narrowing means checking the type inside the code, so TypeScript knows the exact type in that block.

Using typeof

The typeof check is used as a type guard for primitive types.

const print = (value: string | number) => {
if (typeof value === "string") {
return value.toUpperCase();
} else {
return value;
}
};

Inside the if block, value is a string. In the else block, it is a number.

Using instanceof

The instanceof check tells us whether a value was created from a certain class.

const showDate = (x: Date | string) => {
if (x instanceof Date) {
console.log(x.toISOString());
return;
}
const date = new Date(x);
console.log(date.toISOString());
};
Using the in Operator

The in operator checks whether a property exists in an object.

type Bird = { fly: () => void };
type Fish = { swim: () => void };

const move = (animal: Bird | Fish) => {
if ("fly" in animal) {
animal.fly();
return;
}
animal.swim();
};
Conclusion

With typeof, instanceof and in, we can safely work with union types. TypeScript checks our code at compile time, so we catch mistakes early.
