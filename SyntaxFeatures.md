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
