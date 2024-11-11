### STRUCTS IN GOLANG

```Go
type car struct {
  Make string
  Model string
  Height int
  Width int
}

car{ Make: ‘Toyota’, Model: ‘Glanza’, Height: 2.5, Width: 7 }

Nested Struct

type messageToSend struct {
	message   string
	sender    user
	recipient user
}

type user struct {
	name   string
	number int
}

Embedded Struct

type car struct {
  make string
  model string
}

type truck struct {
  // "car" is embedded, so the definition of a
  // "truck" now also additionally contains all
  // of the fields of the car struct
  car
  bedSize int
}

lanesTruck := truck{
  bedSize: 10,
  car: car{
    make: "toyota",
    model: "camry",
  },
}

fmt.Println(lanesTruck.bedSize)

// embedded fields promoted to the top-level, instead of lanesTruck.car.make
fmt.Println(lanesTruck.make)
fmt.Println(lanesTruck.model)




truck{
  bedSize: 10,
  car: car{
    make: "toyota",
    model: "camry",
  },
}


type sender struct {
    user
    rateLimit int
}

type user struct {
   name   string
   number int
}

sender{
	rateLimit: 10000,
	user: user{
	   name:   "Deborah",
	   number: 18055558790,
	},
}

```

```Go

type rect struct {
  width int
  height int
}

// area has a receiver of (r rect)
func (r rect) area() int {
  return r.width * r.height
}

r := rect{
  width: 5,
  height: 10,
}

fmt.Println(r.area())
// prints 50
```


```Go

type authenticationInfo struct {
	username string
	password string
}

func (auth authenticationInfo) getBasicAuth() string {
	return "Authorization: Basic " + auth.username + ":" + auth.password
}


authInfo = authenticationInfo{ username: "Google", password: "12345" }

authInfo.getBasicAuth()

```

### INTERFACES IN GO

Interfaces are collections of method signatures

```Go
type shape interface {
  area() float64
  perimeter() float64
}

type rect struct {
    width, height float64
}
func (r rect) area() float64 {
    return r.width * r.height
}
func (r rect) perimeter() float64 {
    return 2*r.width + 2*r.height
}

type circle struct {
    radius float64
}
func (c circle) area() float64 {
    return math.Pi * c.radius * c.radius
}
func (c circle) perimeter() float64 {
    return 2 * math.Pi * c.radius
}

// So here I can put any circle - 
var c shape   =  circle{ radius: 0.5 }
var r shape = rect{ width: 10, height: 10 }

```

Circle and rect should implement area and perimeter

A type never declares that it implements a given interface. If an interface exists and a type has the proper methods defined, then the type automatically fulfills that interface.

### Slices

#### Capacity

* Each element in a slice is assigned to consecutive memory locations, which makes it quick to read or
write these values. Every slice has a capacity, which is the number of consecutive memory locations reserved. 
This can be larger than the length.

* Each time you append to a slice, one or more values is added to the end of
the slice. Each value added increases the length by one. When the length
reaches the capacity, there’s no more room to put values.

* If you try to add additional values when the length equals the capacity, the append function
uses the Go runtime to allocate a new slice with a larger capacity. The values in the original slice are copied to the new slice, the new values are added to the end, and the new slice is returned.

* When a slice grows via append, it takes time for the Go runtime to allocate new memory and copy the existing data from the old memory to the new. The old memory also needs to be garbage collected. 
For this reason, the Go runtime usually increases a slice by more than one each time it runs out of capacity. 

The rules as of Go 1.14 are to double the size of the slice when the capacity is less than 1,024 and then grow by at least 25%
afterward.

* One common beginner mistake is to try to populate those initial elements using append:

```Go
  x := make([]int, 5)
  x = append(x, 10)
```

The 10 is placed at the end of the slice, after the zero values in positions 0–
4 because append always increases the length of a slice. The value of x is
now [0 0 0 0 0 10], with a length of 6 and a capacity of 10 (the capacity was
doubled as soon as the sixth element was appended).

We can also specify an initial capacity with make:

```Go
  x := make([]int, 5, 10)
```
This creates an int slice with a length of 5 and a capacity of 10.

```
  x := make([]int, 0, 10) // Recommeded way
```

In this case, we have a non-nil slice with a length of 0, but a capacity of 10.
Since the length is 0, we can’t directly index into it, but we can append
values to it:

```
  x := make([]int, 0, 10) // 10 is capacity. 
  x = append(x, 5,6,7,8)
```

The value of x is now [5 6 7 8], with a length of 4 and a capacity of 10.

```
  x := []int{1, 2, 3, 4}
  y := x[:2] //  [1, 2]
  d := x[1:3] // [2, 3]
```

