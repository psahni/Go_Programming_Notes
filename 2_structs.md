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

