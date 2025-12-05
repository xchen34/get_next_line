# Usage Example

To use the `get_next_line` function in your project:

```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main(void)
{
    int fd = open("example.txt", O_RDONLY);
    char *line;

    if (fd < 0)
        return 1;

    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

- Replace `"example.txt"` with the path to your own file.
- Make sure to compile your code with `get_next_line.c` and link necessary libraries if required.
