# I/O in C++

## Streams

- Input and output can be thought of as streams of bytes that are handled by an I/O library
- There are many different kinds of input and output. Some examples include:
  - Data streams (network, files, display devices, etc.)
  - Keyboard interaction
  - GUI interaction

### istream and ostream

- C++ uses the `istream` type to deal with input and the `ostream` type for output
- The `ostream` type:
  - Turns values into character sequences
  - Sends character sequences to console, file, memory, etc.
  - Internally stores data in a buffer before sending to destination
  - Provides features for formatting
  - An example of an `ostream` is `std::cout`
- The `istream` type:
  - Gets character sequences from console, file, memory, etc.
  - Turns character sequences into values
  - Provides features for reading output produced by `ostream`s

### File Streams

- Think of a file as a sequence of bytes
  - The file format is a set of rules that determines what those bytes mean
- An `ostream` converts data from memory into streams of bytes and writes them to disk
- An `istream` takes a stream of bytes from disk and creates data from it

#### Opening and Closing a File

Before reading from or writing to a file, you must open a stream for it first.

The C++ standard library privides tools for this:

- `std::ifstream` is an `istream` for reading from a file
- `std::ofstream` is an `ostream` for writing to a file
- `std::fstream` is an `iostream` that can be used for both reading and writing

Here is an example of opening a file for reading:

```
std::string filename = "test_file.txt";
std::ifstream stream(filename);

if (!stream) {
    std::cout << "ERROR: unable to open file." << std::endl;
}
```

And here is an example of opening a file for writing:

```
std::string filename = "test_file.txt";
std::ofstream stream(filename);

if (!stream) {
    std::cout << "ERROR: unable to open file." << std::endl;
}
```

Notice how similar the two examples are. The check `if (!stream)` checks if the file was opened properly. You can't open a file stream a second time without closing it first.

Files should always be closed before your program terminates. When a file stream goes out of scope, its associated file is closed automatically. It's often a good idea to explicitly call `close()`

#### Reading and Writing a File

Here is an example of reading from a file:

```
std::string filename = "test_file.txt";
std::ifstream stream(filename);

std::string line;
std::vector<std::string> lines;

if (!stream) {
    std::cout << "ERROR: unable to open file." << std::endl;
}
while (stream >> line) {
    lines.push_back(line);
}
```

And here is an example of writing:

```
std::string filename = "test_file.txt";
std::ofstream stream(filename);

if (!stream) {
    std::cout << "ERROR: unable to open file." << std::endl;
}

stream << "Hello world!\n";
```

## I/O Error Handling

An `istream` has four state-checking functions: `good()`, `eof()`, `fail()`, and `bad()`

## Resources

- [Programming: Principles and Practice Using C++ (2nd Edition) by Bjarne Stroustrup](https://www.amazon.com/Programming-Principles-Practice-Using-2nd/dp/0321992784)
- [cppreference](https://en.cppreference.com/w/)
