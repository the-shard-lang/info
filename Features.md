# Features
Here you can read every feature of the Shard programming language.
## Grouping protection levels
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
## Inlining protection levels
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
## Interpolated strings
Just as in any normal language, Shard supports interpolated strings.
```cs
var firstName = "Barack";
var lastName = "Obama";

var message = "Hello, $(firstName) $(lastName)!";
Console.write(message); // Hello, Barack Obama!
```
## Variables
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
## Type inference
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
## Functions
Every normal language should have support for functions, they represent a small block of code that can take arguments and return values. Shard functions are identical to Kotlin functions.
```cs
doStuff();

fun doStuff() {
  Console.write("Hello World!");
}
```
Arguments are declared in parentheses after the function name and separated by a comma.
```cs
logToConsole("Hello", "World!"); // Hello World!

fun logToConsole(message1: str, message2: str) {
  Console.write("$(message1) $(message2)");
}
```
Arguments can have a default value, such arguments will not be required in a function call.
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

fun sqrt(input: flt): flt {
  return input ** 0.5;
}
```
## Inlined functions
Functions in Shard can also be inlined
```cs
Console.write(sqrt(9)); // 3

fun sqrt(input: flt): flt => input ** 0.5;
```
Inlined functions type can be infered
```cs
log(sqrt(9)); // 3

fun sqrt(input: flt) => input ** 0.5; // returns float
fun log(message: str) => Console.write(message); // returns void
```
## Anonymous functions
In Shard you can also declare anonymous functions.
inline declaration
```cs
array.sort((a, b) => [expression]);
```
multiline declaration
```cs
array.sort((a, b) => {
  // logic goes here
});
```
# Namespace
