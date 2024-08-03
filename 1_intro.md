### Intro

Go purpose is to simplify concurrency
Ruby is developer friendly and focussed on dev productivity


Init a project on local machine terminal:-

```Go
  $ go mod init github.com/psahni/module_name
```

* Go code generally runs faster than interpreted languages and compiles faster than other compiled languages like C and Rust


### Structure of Go Program

- package main lets the Go compiler know that we want this code to compile and run as a standalone program, as opposed to being a library that's imported by other programs.

- import fmt imports the fmt (formatting) package. The formatting package exists in Go's 

- standard library and let's us do things like print text to the console.
func main() defines the main function. main is the name of the function that acts as the entry point for a Go program.


### COMPUTERS NEED MACHINE CODE

A computer's CPU only understands its own instruction set, which we call "machine code".

Instructions are basic math operations like addition, subtraction, multiplication, and the ability to save data temporarily.

For example, an ARM processor uses the ADD instruction when supplied with the number 0100 in binary.

* Go is compiled lang

### Why is it generally more simple to deploy a compiled server program?

There are no run time lang dependencies needed

* Go Programs are memory efficient
* Go program uses less memory than Java programs
* They are inbuilt optimized for memory
* C, Rust are more lighter than Go, becz dev has more control
* Go Runtime - This is extra code (small program)  included in executable binary, to delete unused memory at runtime


### Go Variables

```Go
  numCars := 10 // inferred to be an integer

  temperature := 0.0 // temperature is inferred to be a floating point value because it has a decimal point

  var isFunny = true // isFunny is inferred to be a boolean

  Outside of a function (in the global/package scope), every statement begins with a keyword (var, func, and so on) and so the := construct is not available.

  averageOpenRate, displayMessage := 50, "Hello Prashant!" (One line multiple variables)
 
```

### Variable Type casting

```Go
  temperatureInt := 88
  temperatureFloat := float64(temperatureInt)

  mileage, company := 80276, "Tesla"
```

### Recommended data types to use

bool
string
int
uint
byte
rune
float64
complex128

* Constants are declared like variables but use the const keyword. 
* Constants can't use the := short declaration syntax.

```Go
  fmt.Printf - Prints a formatted string to standard out.
  fmt.Sprintf() - Returns the formatted string

  const name = "Saul Goodman"
  msg := fmt.Sprintf("Hi! I am %v", name)
  fmt.Println(msg)
```

```Go
  if height > 6 {
      fmt.Println("You are super tall!")
  } else if height > 4 {
      fmt.Println("You are tall enough!")
  } else {
      fmt.Println("You are not tall enough!")
  }
```

* An if conditional can have an "initial" statement. The variable(s) created in the initial statement are only defined within the scope of the if body.

```
  if INITIAL_STATEMENT; CONDITION {}
```

```Go
if length := getLength(email); length < 1 {
    fmt.Println("Email is invalid")
}
```


* Variables in Go are passed by value (except for a few data types we haven't covered yet). "Pass by value" means that when a variable is passed into a function, that function receives a copy of the variable. The function is unable to mutate the caller's original data.


### Datatypes

```
uint8       unsigned  8-bit integers (0 to 255)
uint16      unsigned 16-bit integers (0 to 65535)
uint32      unsigned 32-bit integers (0 to 4294967295)
uint64      unsigned 64-bit integers (0 to 18446744073709551615)
int8        signed  8-bit integers (-128 to 127)
int16       signed 16-bit integers (-32768 to 32767)
int32       signed 32-bit integers (-2147483648 to 2147483647)
int64       signed 64-bit integers (-9223372036854775808 to 9223372036854775807)
```

https://www.digitalocean.com/community/tutorials/understanding-data-types-in-go

