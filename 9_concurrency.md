### Defer
Useful to run operations after the function complete 
Clean up resources, reset data


#### Read a file

```Go
// Make the buffer, read the file in the buffer
file, err := os.Open("sample.txt")
defer file.close()
```


### Concurrency

* Two types of concurrent code:-
* Threaded: code runs in parallel based on the number of CPU cores
* Asynchronous: code can pause and resume execution. While it is paused, other codes can resume

-> Go automatically chooses the appropriate concurrency method.

### Go routines

This allows functions to run concurrently
Go will automatically select parallel or async execution
New go routines can be created with the go keyword

Imp: a function that starts the routine, and will not wait for the routine to finish, both routine and calling functions will chase to finish

### Channels

One way communication

```Go
channel := make(chan int)

// Send to channel
go func() { channel <-1 }()
go func() { channel <-2 }()

// Receive from channel
first := <- channel
second := <- channel
```


* Channels allow communication between go routines
* Channels can be buffered or unbuffered
* Once you are done with channel, you must close it


### What-exactly-does-runtime-gosched-do ?
`runtime.Gosched()` is a function available in the Go runtime package. It's used to explicitly yield control to the Go scheduler, allowing other Goroutines to run. This simple yet powerful function plays a vital role in managing concurrency.

`runtime.Gosched()` embodies Go's cooperative scheduling model, where Goroutines voluntarily yield control. This non-preemptive approach ensures that Goroutines can work together efficiently.


### Go Run Time

#### Atomic

Two or more processes executing in a system with an illusion of concurrency and accessing shared data may try to change the shared data at the same time. This condition in the system is known as a race condition. To see the sample code for Race Condition in Golang, you can refer to this article.
Atomic package in Golang provides the low-level locking mechanisms for synchronizing access to pointers and integers etc. The atomic/sync package functions are used to fix the race condition.

Code: Check Golang folder

GOOS GOARCH helps us to build binaries for diff platforms

```
 $ go env GOOS GOARCH
```
#### Context
* In Go servers, each incoming request is handled in its own goroutine. Request handlers often start additional goroutines to access backends such as databases and RPC services. The set of goroutines working on a request typically needs access to request-specific values such as the identity of the end user, authorization tokens, and the request’s deadline. When a request is cancelled or times out, all the goroutines working on that request should exit quickly so the system can reclaim any resources they are using.

* At Google, we developed a context package that makes it easy to pass request-scoped values, cancellation signals, and deadlines across API boundaries to all the goroutines involved in handling a request. The package is publicly available as context. This article describes how to use the package and provides a complete working example.

* request scope data - Request scope information can be authentication token, user ID’s, trace ID’s 
https://peter.bourgon.org/blog/2016/07/11/context.html


`WithCancel`
	Returns a cancel function, which when you call, signals the ctx.done channel

`WithDeadline`

`WithTimeout`


```GO
ctx := context.WithValue(context.Background(), "1", "one") // base context 
ctx = context.WithValue(ctx, "2", "two") //derived context fmt.Println(ctx.Value("1")) fmt.Println(ctx.Value("2"))
```





### Links

https://medium.com/@hatronix/mastering-concurrency-with-runtime-gosched-in-go-3b88e2eea07b
https://stackoverflow.com/questions/13107958/what-exactly-does-runtime-gosched-do


