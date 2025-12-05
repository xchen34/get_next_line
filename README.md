# Get Next Line

A function that reads a line from a file descriptor, implementing dynamic buffer management and efficient memory handling.

## 📖 Description

`get_next_line` is a 42 school project that challenges students to write a function that returns a line read from a file descriptor. This project teaches important concepts about:
- Static variables in C
- Dynamic memory allocation
- File descriptor manipulation
- Buffer management

## 🚀 Function Prototype

```c
char *get_next_line(int fd);
```

### Parameters
- `fd`: The file descriptor to read from

### Return Value
- Returns the line read from the file descriptor
- Returns `NULL` if there is nothing else to read or if an error occurred

## 📋 Features

### Mandatory Part
- Read from a file descriptor one line at a time
- Repeated calls to `get_next_line()` should read the text file sequentially
- Function should work with both file and standard input
- The returned line should include the terminating `\n` character (except if EOF is reached)
- Configurable `BUFFER_SIZE` for read() calls

### Bonus Part
- Manage multiple file descriptors simultaneously
- Use only one static variable
- All bonus files are suffixed with `_bonus`

## 🛠️ Compilation

### Mandatory
```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c main.c -o gnl
```

### Bonus
```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line_bonus.c get_next_line_utils_bonus.c main_bonus.c -o gnl_bonus
```

## 💻 Usage

### Read from a file
```bash
./gnl text.txt
```

### Read from standard input
```bash
./gnl
```

## 📝 Example

```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main(void)
{
    int fd;
    char *line;

    fd = open("text.txt", O_RDONLY);
    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return (0);
}
```

## 📂 Project Structure

```
.
├── get_next_line.c              # Main function implementation
├── get_next_line.h              # Header file
├── get_next_line_utils.c        # Helper functions
├── get_next_line_bonus.c        # Bonus implementation
├── get_next_line_bonus.h        # Bonus header file
├── get_next_line_utils_bonus.c  # Bonus helper functions
├── main.c                       # Test main function
├── main_bonus.c                 # Bonus test main function
└── README.md                    # This file
```

## ⚙️ Functions

### Main Functions
- `get_next_line()` - Reads and returns the next line from a file descriptor
- `read_and_add()` - Reads from fd and adds to stock
- `extract_from_stock()` - Extracts a line from the stock
- `clean_extracted_stock()` - Cleans the stock after extraction

### Utility Functions
- `ft_strlen()` - Calculates string length
- `ft_strchr()` - Finds character in string
- `add_to_stock()` - Adds buffer to stock

## 🧪 Testing

Test files are provided:
- `text.txt` - Regular test file
- `text1.txt`, `text2.txt`, `text3.txt`, `text4.txt` - Various test cases
- `gnlTester/` - External tester directory

## 📌 Notes

- The function uses a static variable to keep track of what has been read
- BUFFER_SIZE can be modified during compilation using `-D BUFFER_SIZE=n`
- Memory leaks are handled properly with appropriate free() calls
- The function handles edge cases like empty files and reading errors

## 👤 Author

**leochen** - 42 School Student

## 📄 License

This project is part of the 42 School curriculum.