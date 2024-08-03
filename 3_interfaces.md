### Interfaces

```Go
type employee interface {
	getName() string
	getSalary() int
}

```
Both implement employee interface, so both automatically becomes interface

### INTERFACES ARE IMPLEMENTED IMPLICITLY

A type implements an interface by implementing its methods. Unlike in many other languages, there is no explicit declaration of intent, there is no "implements" keyword.

Implicit interfaces decouple the definition of an interface from its implementation. You may add methods to a type and in the process be unknowingly implementing various interfaces, and that's okay.

So type can fulfill multiple interfaces

```Go
type shape interface {
  area() float64
}
```

If a type in your code implements an area method, with the same signature (e.g. accepts nothing and returns a float64), then that object is said to implement the shape interface.

```Go
type Copier interface {
  Copy(sourceFile string, destinationFile string) (bytesCopied int)
}
```

For readability and clarity

```Go
type expense interface {
	cost() float64
}

type email struct {
	isSubscribed bool
	body         string
	toAddress    string
}

type sms struct {
	isSubscribed  bool
	body          string
	toPhoneNumber string
}

func (s *sms) cost() {

}

func (e *email) cost() {

}

func test (e expense) {
  c, isemail := e.(email)

  if isemail {
    return c.toAddress, e.cost()
  }

}

```

* email and sms both implement cost() function
* We can check on the e which is type of expense interface whether it is sms or email

`value.(type)` -> check the type of value

### Swtich Statements

```Go
func getExpenseReport(e expense) (string, float64) {
	switch v := e.(type) {
	case email:
		return v.toAddress, v.cost()
	case sms:
		return v.toPhoneNumber, v.cost()
	 default:
		return  "", 0.0
	}
}
```

### INTERFACES ARE NOT CLASSES

- Interfaces are not classes, they are slimmer.

- Interfaces don’t have constructors or deconstructors that require that data is created or destroyed.

- Interfaces aren’t hierarchical by nature, though there is syntactic sugar to create interfaces that happen to be supersets of other interfaces.

- Interfaces define function signatures, but not underlying behavior. Making an interface often won’t 

- DRY up your code in regards to struct methods. For example, if five types satisfy the fmt.Stringer interface, they all need their own version  of the String() function.

```Go
type car interface {
	Color() string
	Speed() int
}


type firetruck interface {
	car
	HoseLength() int
}
```

* Above is a kind of inheritance

### Interface Best Practices
https://blog.boot.dev/golang/golang-interfaces/


