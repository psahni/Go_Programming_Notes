### GO Input and Output

- At the fundamental level, every piece of data is just a bunch of bytes.

- Most of what we do when programming is moving data around.

- Moving data is composed of two parts: reading and writing. Go offers us io.Reader and io.Writer abstractions for these operations.

- A Reader is something you can read from, and a Writer is something you can write to.

- As long as something implements io.Reader you can read from it and if it implements io.Writer you can write to it


#### A simple program to read lines

```Go
	in := bufio.NewScanner(os.Stdin)

	for in.Scan() {
		fmt.Println("Scanned Text ", in.Text())
	}
```

### Links

https://medium.com/@andreiboar/fundamentals-of-i-o-in-go-c893d3714deb

https://www.linode.com/docs/guides/creating-reading-and-writing-files-in-go-a-tutorial/