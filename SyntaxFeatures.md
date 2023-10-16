# Syntax & Features
Here you can read about syntax and about every feature of the Shard programming language.
## Feature: Grouping protection levels
In c#, you have to specify a protection level for each non-private member, but Shard takes the protections to a more convenient level by grouping the protection levels.
```cs
class Example {
protected:
  var _speed = 10f;
  var _maxHealth = 100f;

public:
  fun logSpeed() => Console.write(_speed);
  fun logMaxHealth() => Console.write(_maxHealth);
}
```
## Feature: Inlining protection levels
Shard also supports inline protection levels.
```cs
class Example {
protected:
  var _speed = 10f;
  var _maxHealth = 100f;

  public fun logInfo() {
    Console.write(_speed);
    Console.write(_maxHealth);
  }
}
```
## Feature: Interpolated strings
String concatenation can be very inconvenient, so Shard supports interpolated strings.
```cs
var firstName = "Barack";
var lastName = "Obama";

var message = "Hello, $(firstName) $(lastName)!";
Console.write(message); // Hello, Barack Obama!
```
## Syntax: Variables
There are 3 types of variables in Shard.
| variable | explanation |
| -------- | ----------- |
| var | value can be changed anywhere |
| immut | value can be changed only in constructor |
| const | variable is compile time and value cant be changed  |

Usage & declaration
```cs
// [variable] [name]: [type] = [value]
var coins: i32 = 10;
coins++;

immut input: str = Console.read();

const PI: flt = 3.145;
```
Default value
```cs
// [variable] [name]: [type]
var stringDefault: str; // value = "";
var intDefault: i32; // value = 0;
var boolDefault: bool; // value = false;
```
Constants cannot be with default value!
## Feature: Type inference
Always specifying a type for a variable or an argument can be inconvenient and mess up the code, so Shard supports type inference.
```cs
var variable = 10; // type = i32
immut variable = "Hello World!"; // type = str
const variable = true; // type = bool
```
To infer floating-point types, you must use the appropriate token for the type at the end of the number.
| type | token |
| ---- | ----- |
| flt | `f` |
| dob | `d` |
| dec | `m` |
```cs
var variable = 10.5; // type = flt because its the default type for floating point numbers

var variable = 10; // type = i32
var variable = 10f; // type = flt
var variable = 10d; // type = dob
var variable = 10m; // type = dec
```
## Syntax: Functions
```cs
doStuff();

fun doStuff() {
  Console.write("Hello World!");
}
```
Arguments are declared in parentheses after the function name and separated by a comma.
Notice that the argument type is specified before the argument name.
```cs
logToConsole("Hello", "World!"); // Hello World!

fun logToConsole(str message1, str message2) {
  Console.write("$(message1) $(message2)");
}
```
Arguments can have a default value, such arguments will not be required in a function call.
Argument types with a standard value can be inferred.
```cs
logToConsole(); // Hello World!
logToConsole("Hello Shard!"); // Hello Shard!

fun logToConsole(message = "Hello World!") {
  Console.write(message);
}
```
Functions can return a value back to the point where they were called.
```cs
Console.write(sqrt(9)); // 3

fun sqrt(flt input): flt {
  return input ** 0.5;
}
```
## Feature: Inlined functions
Functions in Shard can be inlined.
```cs
Console.write(sqrt(9)); // 3

fun sqrt(flt input): flt => input ** 0.5;
```
Inlined functions type can be inferred.
```cs
log(sqrt(9)); // 3

fun sqrt(flt input) => input ** 0.5; // returns float
fun log(str message) => Console.write(message); // returns void
```
## Syntax: Arrays
```cs
var fruits: str[] = ["apple", "banana", "orange"];
// or with type inference
var fruits = ["apple", "banana", "orange"];
```
There are some built in functions for arrays
```cs
array.removeAll(element); // removes every occurrence of the specified element in an array
array.removeFirst(element); // removes first occurrence of the specified element in an array
array.removeLast(element); // removes last occurrence of the specified element in an array

array.push(element); // adds element to the end of an array
array.pop(); // removes and returns last element of an array

array.push(index, element); // inserts element at the given index
array.pop(index); // removes at the given index
```
## Feature: Array addition
In Shard, you can use the + operator to concatenate arrays or add elements to an array.
```cs
[1, 2] + [3, 4]   // [1, 2, 3, 4]
[1, 2] + 3        // [1, 2, 3]
3 + [1, 2]        // [3, 1, 2]
```
## Feature: Negative indexing
When you need to get the last element in an array, you usually write something like this:
```cs
var array = [1, 2, 3, 4, 5];
var last = array[array.length - 1];

Console.write(last); // 5
```
This can be inconvenient and ugly, so thats why Shard has negative indexing.
```cs
var array = [1, 2, 3, 4, 5];
var last = array[-1];

Console.write(last); // 5
```
## Feature: Array slicing
Works just like in python
```cs

```
