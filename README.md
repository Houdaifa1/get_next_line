<div align="center">

# 📄 get_next_line

**Read a file one line at a time. Sounds simple. It is not.**

![C](https://img.shields.io/badge/language-C-blue?style=for-the-badge&logo=c)
![42](https://img.shields.io/badge/school-42-black?style=for-the-badge)
![Score](https://img.shields.io/badge/score-125%2F100-brightgreen?style=for-the-badge)

</div>

---

## 🧠 What is get_next_line?

`get_next_line` (GNL) is a 42 project that teaches you to read from a file descriptor **one line at a time**, handling any buffer size and multiple file descriptors simultaneously. It forces you to think carefully about **static variables**, **memory management**, and **edge cases**.

Call it once, get line 1. Call it again, get line 2. Until EOF.

---

## 📌 Prototype

```c
char *get_next_line(int fd);
```

Returns the next line from the file descriptor `fd`, including the trailing `\n` (except at EOF if the file doesn't end with one). Returns `NULL` on EOF or error.

---

## ⚙️ Key Concepts

- **Static variables** — preserve state between calls
- **Buffer management** — configurable via `-D BUFFER_SIZE=n`
- **Multiple fd support** — handles simultaneous reads from different files
- **Memory safety** — no leaks, even across partial reads

---

## 🚀 Usage

```bash
git clone https://github.com/Houdaifa1/get_next_line
cd get_next_line
```

Compile with your chosen buffer size:

```bash
gcc -Wall -Werror -Wextra -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c main.c -o gnl
```

Example:

```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main(void)
{
    int fd = open("file.txt", O_RDONLY);
    char *line;

    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return (0);
}
```

---

## 📁 Files

| File | Role |
|------|------|
| `get_next_line.c` | Core logic |
| `get_next_line_utils.c` | Helper functions |
| `get_next_line.h` | Header |
| `get_next_line_bonus.c` | Multi-fd version |
| `get_next_line_utils_bonus.c` | Bonus helpers |

---

<div align="center">
<i>One line at a time. One lesson at a time.</i>
</div>
