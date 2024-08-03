```Go
type Season int64

const (
	Summer Season = 0
	Autumn Season = 1
	Winter Season = 2
	Spring Season = 3
)

const (
	Summer Season = iota
	Autumn
	Winter
	Spring
)

func (s Season) String() string {
	switch s {
	case Summer:
		return "summer"
	case Autumn:
		return "autumn"
	case Winter:
		return "winter"
	case Spring:
		return "spring"
	}
	return "unknown"
}

```

https://www.sohamkamani.com/golang/enums/#google_vignette
