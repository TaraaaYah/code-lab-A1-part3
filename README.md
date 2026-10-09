# code-lab-A1-part3
# Book Manager

A C++ console program for managing a small library of books, using object-oriented programming. Users can view, search, borrow, and return books through a menu-driven interface, with changes saved back to a text file.

Created as part of the Programming Skills Portfolio assessment for CodeLab II (Bath Spa University).

## Features

- Loads book records from an external text file (`bookData.txt`)
- View all books, with title, author, pages, ID, and availability status
- Search for a book by ID
- Borrow and return books, with changes saved immediately
- Input validation for both menu choices and book data (skips malformed records rather than crashing)
- Data persists between runs via file read/write

## How It Works

### `Book` class
Represents a single book. Keeps its data (`title`, `author`, `pages`, `id`, `available`) private, exposing it only through getter methods and a `display()` function. Borrowing and returning are handled by the class itself (`borrowBook()`, `returnBook()`), which check the current availability before changing it.

### Supporting functions

| Function | Purpose |
|---|---|
| `loadBooks()` | Reads `bookData.txt`, splits each line into fields with `stringstream`, validates them, and constructs a `Book` object per valid line |
| `saveBooks(vector<Book>&)` | Writes the current list of books back to `bookData.txt`, called after any borrow/return |
| `findBookByID(vector<Book>&, string)` | Searches for a book by ID, returning its index or `-1` if not found |

`main()` loads the books into a `vector<Book>` and runs a menu loop (view all / search / borrow / return / quit) until the user chooses to exit.

## Book Data Format

Each book is stored on its own line in `bookData.txt`, as comma-separated values:

```
title,author,pages,id,available
```

Example:

```
The Hobbit,J.R.R. Tolkien,310,001,true
1984,George Orwell,328,002,false
```

> Note: titles/authors containing commas are not currently supported, since the file uses a plain comma-separated format.

## Example Output

```
===== BOOK MANAGER =====
1. View all books
2. Search book by ID
3. Borrow book by ID
4. Return book by ID
5. Quit
Enter your choice: 3
Enter book ID (e.g. 001): 001
Book borrowed successfully!
```

## Build & Run

```bash
g++ -o book_manager main.cpp
./book_manager
```

Ensure `bookData.txt` is in the same directory as the executable.

## Author

Tara ([TaraaaYah](https://github.com/TaraaaYah))


