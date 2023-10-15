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
Variables are used to store the date in the program, there are 2 types of variables in Shard.
| varaible | explanation |
| -------- | ----------- |
| var | value can be changed anywhere |
| const | value can be changed only in constructor |

full declaration
```cs
// [variable] [name]: [type] = [value]
var fif: int32 = 10;
const kafif: str = "kafif";
```
default value
```cs
// [variable] [name]: [type]
var stringDefault: str; // value = "";
const intDefault: int32; // value = 0;
```
Note that a variable must necessarily define a type or value.
## Type inference
Always specifying a type for a variable or an argument can be inconvenient and mess up the code, so Shard supports type inference.
```cs
var variable = 10; // type = int32
var variable = "Hello World!"; // type = str
var variable = true; // type = bool
```
To infer floating-point types, you must use the appropriate token for the type at the end of the number.
| type | token |
| ---- | ----- |
| flt | `f` |
| dob | `d` |
| dec | `m` |
```cs
var variable = 10.5; // type = flt because flt is the default type for floating point numbers

var variable = 10; // type = int32
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
# Classes
# Objects
In c#, if you need to create a simple container for variables to conveniently pass them as an argument, you need to create a large structure, Shard takes it to a more convenient level with objects.
```cs
object NoiseSettings {
}
```
# If else statement
```cs
if gray && orangeEyes {
  cat = "gosha";
} 
else if brown && greenEyes {
  cat = "shotya";
}
else {
  cat = "undefined";
}
```
### Switch statement
```cs
switch colorIdx {
  case 0:
    outputColor = "red";
  case 1:
    outputColor = "green";
  case 2:
    outputColor = "blue";
  default:
    outputColor = "undefined";
}
```
