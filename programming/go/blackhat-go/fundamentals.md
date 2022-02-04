# Fundamentals

### Decrease size binary

By default, the produced binary file contains debugging information and the symbol table. This can bloat the size of the file. To reduce the file size, you can include additional flags during the build process to strip this information from the binary. For example, the following command will reduce the binary size by approximately 30 percent:

```
$ go build -ldflags "-w -s"
```

### **Format Code**

The go fmt command automatically formats your source code. For example, running go fmt /path/to/your/package will style your code by enforcing the use of proper line breaks, indentation, and brace alignment
