### Errors

When something can go wrong in a function, that function should return an error as its last return value. Any code that calls a function that can return an error should handle errors by testing whether the error is nil.


```Go
cost1, err1 := sendSMS(msgToCustomer)

if (err1 != nil) {
   return 0.0, err1
}

```
