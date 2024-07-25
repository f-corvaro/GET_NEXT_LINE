<h1 align="center">
<a href="https://github.com/f-corvaro/GET_NEXT_LINE"><img src="https://github.com/f-corvaro/GET_NEXT_LINE/blob/main/.extra/gnl.png"></a>
</h1>

<p align="center">
	<b><i>"Line-by-Line File Reader"</i></b><br>
</p>
<p align="center" style="text-decoration: none;">
    <a href="https://github.com/f-corvaro/GET_NEXT_LINE"><img alt="GitHub code size in bytes" src="https://img.shields.io/github/languages/code-size/f-corvaro/GET_NEXT_LINE?color=blueviolet" /></a>
    <a href="https://github.com/f-corvaro/GET_NEXT_LINE"><img alt="Code language count" src="https://img.shields.io/github/languages/count/f-corvaro/GET_NEXT_LINE?color=yellow" /></a>
    <a href="https://github.com/f-corvaro/GET_NEXT_LINE"><img alt="GitHub top language" src="https://img.shields.io/github/languages/top/f-corvaro/GET_NEXT_LINE?color=blueviolet" /></a>
    <a href="https://github.com/f-corvaro/GET_NEXT_LINE"><img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/f-corvaro/GET_NEXT_LINE?color=yellow" /></a>
</p>

<div align="center">

v10 | v12
:-------------------------:|:-------------------------:
[![subject-old](https://img.shields.io/badge/subject-get_next_line-blueviolet)](https://github.com/f-corvaro/GET_NEXT_LINE/blob/main/.extra/en.subject.pdf) | [![subject-new](https://img.shields.io/badge/subject-get_next_line-blueviolet)](https://github.com/f-corvaro/GET_NEXT_LINE/blob/main/.extra/en.subject(new).pdf)

</div>

<div align="center">
<table><tr><td>This guide is made for the subject v10, there aren't differences between the two subjects</td></tr></table>
</div>

</p>
<br>

<h3 align="center">Index</h3>

<p align="center">
 <a href="#introduction-to-get_next_line">Introduction to `get_next_line()`</a><br>
 <a href="#folder-structure">Folder Structure</a><br>
 <a href="#project-requirements---mandatory-part">Project Requirements - Mandatory Part</a><br>
 <a href="#required-files">Required Files</a><br>
 <a href="#function-prototype">Function Prototype</a><br>
 <a href="#allowed-external-functions">Allowed External Functions</a><br>
 <a href="#expected-function-behavior">Expected Function Behavior</a><br>
 <a href="#compilation-option">Compilation Option</a><br>
 <a href="#project-requirements---bonus-part">Project Requirements - Bonus Part</a><br>
 <a href="#theoretical-background">Theoretical Background</a><br>
 <a href="#string-manipulation">String Manipulation</a><br>
 <a href="#data-structures">Data Structures</a><br>
 <a href="#arrays">Arrays</a><br>
 <a href="#linked-lists">Linked Lists</a><br>
 <a href="#loop-control-and-flow">Loop Control and Flow</a><br>
 <a href="#memory-layout-of-c-programs">Memory Layout of C Programs</a><br>
 <a href="#detailed-segmentation-of-program-memory">Detailed Segmentation of Program Memory</a><br>
 <a href="#understanding-buffer_size-in-memory-management">Understanding `BUFFER_SIZE` in Memory Management</a><br>
 <a href="#garbage-collection-and-memory-fragmentation">Garbage Collection and Memory Fragmentation</a><br>
 <a href="#file-descriptors">File Descriptors</a><br>
 <a href="#standard-file-descriptors">Standard File Descriptors</a><br>
 <a href="#error-handling">Error Handling</a><br>
 <a href="#closing-file-descriptors">Closing File Descriptors</a><br>
 <a href="#end-of-line-detection">End-of-Line Detection</a><br>
 <a href="#static-variables">Static Variables</a><br>
 <a href="#code-optimization">Code Optimization</a><br>
 <a href="#into-the-code">Into the code</a><br>
 <a href="#evaluation">Evaluation</a><br>
 <a href="#testing-mandatory-part">Testing mandatory part</a><br>
 <a href="#testing-bonus-part">Testing bonus part</a><br>
 <a href="#testing-with-gnltester">Testing with gnlTester</a><br>
 <a href="#correction-sheet">Correction Sheet</a><br>
 <a href="#moulinette-feedback">Moulinette Feedback</a><br>
 <a href="#developed-skills">Developed Skills</a><br>
 <a href="#references">References</a><br>
 <a href="#support-and-contributions">Support and Contributions</a><br>
 <a href="#author">Author</a><br>
</p>
<br>

## Introduction to `get_next_line()`

<p align="justify">

The `get_next_line()` function stands out as an essential tool for reading lines from a file descriptor without prior knowledge of the line's length. This capability is particularly beneficial for processing large files or those with variable line lengths. Upon execution, it returns a pointer to a buffer that contains the read line, or `NULL` if no more lines are available. This function is a significant addition to our library (LIBFT), enhancing our file handling capabilities.

Key concepts central to this project include understanding static variables and the intricacies of file descriptor management. The use of global variables, the `GET_NEXT_LINE` function itself, and `lseek()` are strictly prohibited to ensure compliance with project guidelines. Moreover, the function is designed to handle errors gracefully, preventing unexpected terminations such as segmentation faults, bus errors, double frees, and other undefined behaviors. It is imperative to manage heap-allocated memory efficiently, ensuring proper release when no longer needed. Through iterative calls, the `get_next_line` function facilitates the sequential reading of a text file associated with a given file descriptor, one line at a time.

</p>
<br>

## Folder Structure

<p align="justify">

```
.
├── 01-get_next_line
│   ├── get_next_line
│   │   ├── file.txt
│   │   ├── file2.txt
│   │   ├── file3.txt
│   │   ├── get_next_line_bonus.c
│   │   ├── get_next_line_bonus.h
│   │   ├── get_next_line_utils_bonus.c
│   │   ├── get_next_line_utils.c
│   │   ├── get_next_line.c
│   │   └── get_next_line.h
│   └── README.md
```

<br>

## Project Requirements - Mandatory Part

### Required Files 

<p align="justify">

Submit the following files:
- `get_next_line.c`: Contains the core logic for the `get_next_line` function.
- `get_next_line.h`: The header file, which includes the prototype of `get_next_line` and any necessary includes.
- `get_next_line_utils.c`: This file may contain any helper functions used by your `get_next_line` implementation.

</p>

### Function Prototype

<p align="justify">

The prototype for the `get_next_line` function is as follows:
- `char *get_next_line(int fd);`
  - `fd` is the file descriptor from which to read.

</p>

### Allowed External Functions

<p align="justify">

You may only use the following external functions within your project:
- `free()`
- `malloc()`
- `read()`

</p>

### Expected Function Behavior

<p align="justify">

- **Return Value**: The function should return the line that has been read. If there is nothing left to read or an error occurs, it should return `NULL`.
- **Line Termination**: The returned line must include the terminating newline character (`\n`), except in cases where the end of the file is reached and it does not end with a newline character.

</p>

### Compilation Option

<p align="justify">

- Use the `-D BUFFER_SIZE=n` option when compiling your project. This option defines the buffer size for the `read()` function. Your project must compile both with and without this flag. You are free to choose a default buffer size that suits your implementation.

</p>
<br>

## Project Requirements - Bonus Part

<p align="justify">

The bonus section of this project introduces an advanced challenge: implementing the `get_next_line()` function with the constraint of using only a single static variable. This requirement pushes the boundaries of efficient memory and state management within your code. For the bonus evaluation, you are expected to submit three specific files: `get_next_line_bonus.c`, `get_next_line_bonus.h`, and `get_next_line_utils_bonus.c`.

It's crucial to understand that the bonus part will be considered only if the mandatory section of the project is flawlessly completed. "Flawless" implies that every aspect of the mandatory requirements has been fully met and functions correctly without any issues. If the mandatory criteria are not entirely satisfied, the bonus submissions will not be reviewed.

A key feature of the bonus `get_next_line()` function is its ability to handle multiple file descriptors (fd) simultaneously. This means that if you're reading from file descriptors 3, 4, and 5, the function should be capable of maintaining the reading sequence for each fd independently, allowing for seamless switching between fds without losing track of their respective reading positions. The choice of `static char *str[4096];` as the static variable is strategic, aligning with the C standard that mandates compilers to support line lengths of at least 4096 characters. This decision, while adhering to the standard, also takes into consideration the capabilities of modern compilers, which typically do not impose a limit on line size, bounded only by the constraints of available memory.

</p>
<br>

## Theoretical Background

<p align="justify">

The `get_next_line` project involves several key concepts and system calls that are pivotal for handling file operations in C. It builds upon foundational knowledge from the C piscine and LIBFT project, including:

</p>

### Data Structures

<p align="justify">

Data structures are an essential component of the `get_next_line` project. They provide a way to organize and store data efficiently, allowing for easy access and manipulation. In the context of `get_next_line`, data structures can be used to store the lines read from a file, ensuring that they are easily accessible for further processing. One commonly used data structure for this purpose is a linked list.

</p>

#### Arrays

<p align="justify">

Arrays are a fundamental data structure in programming, allowing for the storage of multiple elements of the same type in a contiguous block of memory. In the context of the `get_next_line` project, arrays can be used to store and manipulate characters read from a file. By allocating an array with a fixed size, the function can efficiently read and process chunks of data from the file, ensuring that the lines are correctly extracted. Arrays provide random access to elements, allowing for easy indexing and retrieval of specific characters. Additionally, arrays can be used to store and manage pointers to dynamically allocated memory, ensuring efficient memory management within the `get_next_line` implementation. 

</p>

#### Linked Lists

<p align="justify">

Linked lists are a valuable data structure for managing and organizing data in the `get_next_line` project. They offer dynamic memory allocation, efficient insertion and deletion operations, and the ability to handle variable-length data. Each node in a linked list represents a line of text, and the nodes are connected through pointers, allowing for easy traversal and manipulation of the data. By utilizing linked lists in the `get_next_line` implementation, the function can effectively manage and process the lines read from the file, ensuring efficient storage and retrieval of the data.

</p>
<br>

### String Manipulation

<p align="justify">

String manipulation is a fundamental aspect of the `get_next_line` project. The function is designed to read a file line by line, and string manipulation techniques are essential for processing and extracting the desired data. Functions like `strlen`, `strcpy`, `strcat`, and `strncpy` can be used to manipulate strings, allowing for operations such as finding the length of a string, copying or concatenating strings, and extracting substrings. Additionally, functions like `strchr` and `strstr` can be used to search for specific characters or substrings within a string. Understanding and effectively utilizing these string manipulation functions is crucial for implementing the `get_next_line` function and achieving accurate and efficient file reading functionality.

</p>
<br>

### Loop Control and Flow

<p align="justify">

Loop control and flow are essential concepts in the `get_next_line` project. The `get_next_line` function needs to read a file line by line, and loop control is used to iterate through the file and extract each line. A common approach is to use a `while` loop that continues until the end of the file is reached or an error occurs. Within the loop, the function reads characters from the file and checks for end-of-line characters to identify the end of each line. Once a line is extracted, it can be processed or stored for further use. Loop control and flow ensure that the `get_next_line` function operates correctly, reading and processing each line in the file until the end is reached or an error occurs.

</p>
<br>

### Memory Layout of C Programs

<p align="justify">

The memory architecture of C programs is intricately designed, comprising several segments that each play an important role in the program's lifecycle. This architecture is not just a foundation for efficient program execution but also a bulwark for implementing security measures to safeguard the program's memory space.

</p>

#### Detailed Segmentation of Program Memory

<p align="justify">

- **Text Segment**: Also known as the code segment, this area houses the executable instructions of the program. It's typically marked as read-only to prevent tampering with the program's code during execution. Sharing this segment between processes optimizes memory usage, especially for frequently used programs.

- **Initialized Data Segment**: This segment stores global and static variables that have been explicitly initialized by the programmer. Unlike the text segment, this area is writable, enabling runtime modifications of these variables. It's further divided into read-only and read-write sections based on the initialization characteristics.

- **Uninitialized Data Segment (BSS)**: Standing for "Block Started by Symbol," the BSS segment encompasses global and static variables that are either uninitialized or initialized to zero. The operating system zeroes out this segment before the program starts, ensuring a clean slate for these variables.

- **Heap**: The heap area is dedicated to dynamic memory allocation, controlled at runtime through functions like `malloc`. It expands upwards towards higher memory addresses, providing a flexible space for memory allocation as required by the program's execution dynamics.

- **Stack**: In contrast, the stack segment caters to static memory allocation, which includes local variables, function parameters, and return addresses. It grows in the opposite direction of the heap, downwards towards lower memory addresses. The stack is essential for the orderly execution of function calls and returns, with each call generating a new frame on the stack.

Understanding the nuanced interplay between these segments is crucial for C programmers. It aids in optimizing memory usage, debugging complex issues, and fortifying programs against common security threats like buffer overflows.

</p>

#### Understanding `BUFFER_SIZE` in Memory Management

<p align="justify">

The `BUFFER_SIZE` parameter plays a pivotal role in memory management, particularly in functions that read from files or streams. It determines the size of the buffer, in bytes, that a program allocates for reading data. This parameter directly influences the efficiency and performance of data handling operations. A larger `BUFFER_SIZE` can reduce the number of read operations required by allowing more data to be read in a single operation, potentially speeding up the process for large files. However, it also means higher memory consumption, which might not be ideal for memory-constrained environments. Conversely, a smaller `BUFFER_SIZE` minimizes memory usage but can lead to increased read operations, which might slow down the program due to the overhead associated with each read call. Balancing the `BUFFER_SIZE` is thus essential for optimizing both performance and memory usage, making it a critical consideration in the design and implementation of efficient C programs.

</p>

#### Garbage Collection and Memory Fragmentation

<p align="justify">

Unlike languages with built-in garbage collection mechanisms, C requires manual memory management. Programmers must explicitly allocate and free memory using functions like `malloc` and `free`. This approach necessitates a disciplined management strategy to avoid memory leaks, where unneeded memory is not reclaimed, potentially leading to inefficient memory use and exhaustion of resources. 

Memory fragmentation is another challenge in memory management, manifesting in two forms: external and internal fragmentation. External fragmentation occurs when free memory is split into small, scattered blocks, making it difficult to find a contiguous block for new allocations despite having sufficient total free memory. Internal fragmentation happens when allocated memory blocks are larger than necessary, leading to wasted space within those blocks. Addressing these issues involves strategies like memory compaction, using memory pools, or custom allocators to minimize wasted space and improve allocation efficiency. Incorporating an understanding of these concepts is vital for optimizing memory usage and managing the complexities of dynamic memory allocation in C programs.

</p>
<br>

### File Descriptors

<p align="justify">

In the context of the `get_next_line` project, file descriptors play a crucial role in reading data from files. A file descriptor is a unique identifier assigned by the operating system to each open file. It serves as a reference to the file when performing operations like reading or writing. In the `get_next_line` function, file descriptors are used to specify the source from which data should be read. By passing the appropriate file descriptor as a parameter to the `read` function, the function can retrieve data from the specified file. `read` function allows data to be read from a file descriptor into a buffer. The `read` function takes three parameters: the file descriptor, a pointer to the buffer where the data will be stored, and the maximum number of bytes to read. It returns the number of bytes read, which can be zero at the end of the file or -1 in case of an error. By calling the `read` function in a loop, the `get_next_line` function can read the file line by line, processing the data as needed. This allows the `get_next_line` function to handle multiple file descriptors simultaneously, maintaining the reading sequence for each file independently. Understanding file descriptors is essential for efficient file handling and ensuring the correct retrieval of data in the `get_next_line` implementation.

</p>

#### Standard File Descriptors

<p align="justify">

There are three standard file descriptors that are automatically opened when a program starts:
- **Standard Input (stdin)**: File descriptor 0, used for reading input.
- **Standard Output (stdout)**: File descriptor 1, used for writing output.
- **Standard Error (stderr)**: File descriptor 2, used for writing error messages.

</p>

#### Error Handling

<p align="justify">

When working with file descriptors, it is important to handle errors appropriately. Functions like `open` and `read` return `-1` if an error occurs. Checking the return values of these functions and using `errno` to determine the specific error can help in diagnosing and handling issues effectively. By implementing robust error handling mechanisms, the `get_next_line` function can handle unexpected situations and ensure the reliability and stability of the file reading process.

</p>

#### Closing File Descriptors

<p align="justify">

To prevent resource leaks, it is crucial to close file descriptors when they are no longer needed. The `close` function is used for this purpose. Failing to close file descriptors can lead to a situation where the system runs out of file descriptors, preventing new files from being opened.

By incorporating these additional details, you gain a more comprehensive understanding of file descriptors, their standard types, error handling, and the importance of proper resource management in the `get_next_line` project.

</p>
<br>

### End-of-Line Detection

<p align="justify">

End-of-line detection involves identifying the end of a line in a file and extracting the line for further processing. In many text files, lines are terminated by special characters, such as the newline character (`\n`). The `get_next_line` function needs to detect these end-of-line characters and extract the corresponding line. This can be achieved by reading the file character by character and checking for the presence of end-of-line characters. Once an end-of-line character is detected, the function can extract the line and return it for further processing. End-of-line detection is crucial for accurately reading and processing text files in the `get_next_line` project, ensuring that lines are correctly identified and processed.

</p>
<br>

### Static Variables

<p align="justify">

Static variables play a crucial role in the implementation of the `get_next_line` function. A static variable is a variable that retains its value across multiple function calls. In the context of `get_next_line`, static variables are used to keep track of the current position in the file and the buffer that stores the read data. By declaring these variables as static, their values are preserved between function calls, allowing the function to resume reading from where it left off. This is particularly useful when reading large files or when the function is called multiple times to read from different files. Static variables provide a convenient way to maintain state within the function without the need for global variables, ensuring encapsulation and modularity. Understanding the concept of static variables is essential for effectively implementing the `get_next_line` function and achieving efficient and reliable file reading functionality.

</p>
<br>

### Code Optimization

<p align="justify">

Code optimization is an important consideration in the `get_next_line` project to ensure efficient and performant file reading. Optimizing the code involves identifying and eliminating any unnecessary operations or redundant code that may impact the overall performance. Techniques like loop unrolling, reducing function calls, and minimizing memory allocations can significantly improve the execution speed and resource usage of the `get_next_line` function. Additionally, optimizing the algorithm used for reading and processing the file can lead to significant performance gains. By carefully analyzing the code and making targeted optimizations, the `get_next_line` function can achieve optimal performance and enhance the overall efficiency of the file reading process.

</p>
<br>

### Into the code

The code for the `get_next_line` project involves several important elements. Firstly, the use of `ssize_t` is highlighted, which is a data type capable of storing either a byte count or an error indication (-1), making it suitable for functions that perform read operations or return sizes. It's specifically designed to accommodate the range of values from -1 to SSIZE_MAX, ensuring that both successful outcomes and errors can be effectively communicated. The `read` function, with the prototype `ssize_t read(int fd, void *buf, size_t count);`, is essential for reading data from a file descriptor into a buffer. It returns the number of bytes read, which can be zero at the end of the file or -1 in case of an error, with `count` specifying the maximum number of bytes to read. This function is crucial for file I/O operations, allowing for direct interaction with files at a low level. Additionally, the `open` function is used to open files for reading, writing, or both, identified by a file descriptor—a small, non-negative integer. The function's syntax, `int open(const char *pathname, int flags);`, includes a pathname to the target file and flags that determine the file access mode. Flags like `O_RDONLY` for read-only access are combined using the `|` operator to specify multiple options. These elements are integral to the project, facilitating direct and efficient manipulation of files within the C programming environment.

</p>
<br>

## Evaluation Process

### Testing mandatory part

<p align="justify">

To test the mandatory part of the project, you only need to edit the `get_next_line.c` file and uncomment the main function. The `get_next_line` function will read from the `file.txt` file provided. To compile and run the program, use the following command (replace "xx" with the desired buffer size):

```shell
gcc -Wall -Werror -Wextra -D BUFFER_SIZE=xx get_next_line.c get_next_line_utils.c && ./a.out
```

Additionally, ensure that the code works without the `-D BUFFER_SIZE=xx` flag, as it must function correctly in both scenarios.

```shell
gcc -Wall -Werror -Wextra get_next_line.c get_next_line_utils.c && ./a.out
```

### Memory Leak Detection with Valgrind

To find memory leaks and errors, I used `Valgrind`. Below are the steps for installation and usage:

#### Installation

Depending on your Linux distribution, use one of the following commands to install Valgrind:

```shell
sudo apt install valgrind  # Ubuntu, Debian, etc.
sudo yum install valgrind  # RHEL, CentOS, Fedora, etc.
sudo pacman -Syu valgrind  # Arch, Manjaro, Garuda, etc.
sudo pkg ins valgrind      # FreeBSD
```

#### Usage

To check for memory leaks and errors, use the following Valgrind command:

```shell
valgrind --leak-check=full --show-leak-kinds=all --track-origins=yes -s ./a.out
```

- `--leak-check=full`: Perform a detailed memory leak check.
- `--show-leak-kinds=all`: Show all kinds of leaks, including definitely lost, indirectly lost, possibly lost, and still reachable.
- `--track-origins=yes`: Track the origins of uninitialized values.
- `-s`: Provide a summary of the leak check.
- ADDITIONAL `--log-file`: Directs Valgrind's output to a specified file. This is useful for preserving extensive output that exceeds terminal capacity, allowing for easier review and analysis.

</p>
<br>

### Testing bonus part

<p align="justify">

To test the bonus part of the project, follow these steps:

1. Edit the `get_next_line_bonus.c` file and uncomment the main function.
2. The `get_next_line` function will read from the `file.txt`, `file2.txt`, and `file3.txt` files provided.

To compile and run the program, use the following command (replace "xx" with the desired buffer size):

```shell
gcc -Wall -Werror -Wextra -D BUFFER_SIZE=xx get_next_line_bonus.c get_next_line_utils_bonus.c
```

Additionally, ensure that the code works without the `-D BUFFER_SIZE=xx` flag, as it must function correctly in both scenarios.

</p>
<br>

### Testing with gnlTester

<p align="justify">

I utilized the [gnlTester](https://github.com/Tripouille/gnlTester) developed by [Tripouille](https://github.com/Tripouille) for testing. It's straightforward to use:

1. Navigate to your `get_next_line` directory (e.g., `~/fcorvaro/Desktop/get_next_line`).

2. Clone the gnlTester repository into your `get_next_line` directory using:

  ```shell
  git clone git@github.com:Tripouille/gnlTester.git
  ```

3. Change directory to  `gnlTester`

4. Execute the tests with one of the following commands:

  ```shell
  make m # to run mandatory tests.
  make b # to run bonus tests.
  make a # to run mandatory tests and bonus tests.
  ```

Keep in mind that you can adjust the timeout value in the Makefile for more thorough testing. For a comprehensive evaluation, consider running all tests with Valgrind on Linux (e.g., `valgrind --leak-check=full --show-leak-kinds=all --track-origins=yes -s make m`). Remember, while this tester is a useful tool for validation, it should not be considered the definitive measure of correctness.

The expected output can be found here: [output.txt](https://github.com/f-corvaro/GET_NEXT_LINE/blob/main/.extra/output.txt)

</p>
<br>

### Correction Sheet

<a href="https://github.com/f-corvaro/GET_NEXT_LINE"><img width="650" src="https://github.com/f-corvaro/GET_NEXT_LINE/blob/main/.extra/cs1.png">

<a href="https://github.com/f-corvaro/GET_NEXT_LINE"><img width="650" src="https://github.com/f-corvaro/GET_NEXT_LINE/blob/main/.extra/cs2.png">

<a href="https://github.com/f-corvaro/GET_NEXT_LINE"><img width="650" src="https://github.com/f-corvaro/GET_NEXT_LINE/blob/main/.extra/cs3.png">

<br>

### Moulinette Feedback

<p align="justify"> 

<a href="https://github.com/f-corvaro/GET_NEXT_LINE"><img src="https://github.com/f-corvaro/GET_NEXT_LINE/blob/main/.extra/Moulinette_gnl.png">

</p>
<br>

## Developed Skills

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=git,c,vim,vscode" />
  </a>
</p><br>

## References

- [Understanding Static Variables in C](https://www.geeksforgeeks.org/static-variables-in-c/)
- [Exploring Memory Layout in C Programs](https://www.geeksforgeeks.org/memory-layout-of-c-program/)
- [Using Valgrind to Identify Memory Leaks](https://stackoverflow.com/questions/5134891/how-do-i-use-valgrind-to-find-memory-leaks)

I used additional references but do not recall their specific sources.

<br>

## Support and Contributions

<p align="center">
If you find this repository helpful, please consider starring it to show your support. Your support is greatly appreciated!</p>

<p align="center">
<a href="https://ko-fi.com/fcorvaro"><img width="180" img align="center" src="https://github.com/f-corvaro/42.common_core/blob/main/.extra/support-me-ko-fi.svg"><alt=""></a>
<a href="https://github.com/sponsors/f-corvaro"><img width="180" img align="center" src="https://github.com/f-corvaro/42.common_core/blob/main/.extra/support-me-github.svg"><alt=""></a>

<br>

## Author

<p align="center"><a href="https://profile.intra.42.fr/users/fcorvaro"><img style="height:auto;" src="https://avatars.githubusercontent.com/u/102758065?v=4" width="100" height="100"alt=""></a>
<p align="center">
<a href="mailto:fcorvaro@student.42roma.it"><kbd>Email</kbd><alt=""></a>
<a href="https://github.com/f-corvaro"><kbd>Github</kbd><alt=""></a>
<a href="https://www.linkedin.com/in/f-corvaro/"><kbd>Linkedin</kbd><alt=""></a>
<a href="https://42born2code.slack.com/team/U050L8XAFLK"><kbd>Slack</kbd><alt=""></a>

<hr/>