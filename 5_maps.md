### Map

```Go
colors := map[string]string{
   "red":   "#ff0000",
    "green": "#4bf745",
}
	
fmt.Println(colors)

```

```Go
type Path []Point
			
func (path Path) Distance() float64 {				
  sum := 0.0
    for i := range path {		
      if i > 0 {
            sum += path[i-1].Distance(path[i])
    
    } 
  }
  return sum 
} 

```

```Go
  perim := Path{ {1, 1}, {5, 1}, {5, 4}, {1, 1} }
  fmt.Println(perim.Distance())
```


### Using Struct as Map Keys

It’s obvious that strings, ints, and other basic types should be available as map keys, but perhaps unexpected are struct keys. Struct can be used to key data by multiple dimensions. For example, this map of maps could be used to tally web page hits by country:

```Go
  hits := make(map[string]map[string]int)
```

This is map of string to (map of string to int). Each key of the outer map is the path to a web page with its own inner map. Each inner map key is a two-letter country code. This expression retrieves the number of times an Australian has loaded the documentation page:

```Go
func add(m map[string]map[string]int, path, country string) {
    mm, ok := m[path]
    if !ok {
        mm = make(map[string]int)
        m[path] = mm
    }
    mm[country]++
}
add(hits, "/doc/", "au")
```

* On the other hand, a design that uses a single map with a struct key does away with all that complexity:

```Go
type Key struct {
    Path, Country string
}
hits := make(map[Key]int)
```

When a Vietnamese person visits the home page, incrementing (and possibly creating) the appropriate counter is a one-liner:


```Go
  hits[Key{"/", "vn"}]++
```

```Go
n := hits[Key{"/ref/spec", "ch"}]
```

### Maps are reference types

Map types are reference types, like pointers or slices, and so the value of m above is nil; it doesn't point to an initialized map. A nil map behaves like an empty map when reading, but attempts to write to a nil map will cause a runtime panic; don't do that. To initialize a map, use the built in make function:

Example:-
https://github.com/inancgumus/learngo/blob/master/26-pointers/exercises/04-simplify/solution/main.go