### Generics in GO

```Go
func Sum01[N int | int32 | int64 | float64 | float32](v []N) N{
  var total N
  for _, tV := range v{
    total += tV
  }
  return total
}

```

We define an interface with the same data types, our generic is called ‘Number’.

```Go
type Number interface{
  int | int32 | int64 | float64 | float32
}
```


```Go
func Sum02[N Number](v []N) N{

var total N

for _, tV := range v {
 total += tV
}
  return total
}

v1 := []float64{1.3,5.45,12.223,6.92,78.102}
v2 := []int32{9,23,1,23,8,98}

fmt.Println(Sum02(v1))
fmt.Println(Sum02(v2))

```

### ANY Type

```Go
func anyType[N any](v1, v2 N){
  fmt.Println(v1, v2)
}

anyType(1,1)
anyType("1","1")

anyType(1,"1") // Error. You have to send the same type.mismatched types untyped int and untyped string (cannot infer N)

// Solution:-
func anyTypeTwo[N1 any, N2 any](v1 N1, v2 N2){
 fmt.Println(v1, v2)
}

```
