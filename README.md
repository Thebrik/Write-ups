# Cybersecurity CTF Writeups

Hi, I’m Debrik 👋  
I have solved 75+ CTF rooms on TryHackMe and VulnHub and documented my learning through detailed writeups.

## 🔥 Featured Writeups

- Blue – TryHackMe Walkthrough  
- Ice – TryHackMe Walkthrough  

## ✍️ Medium Articles
I have published 18+ cybersecurity writeups covering:
- CTF Walkthroughs  
- Web vulnerabilities (XSS, SQL Injection, IDOR)  
- Privilege Escalation  

👉 Read here: https://medium.com/@debrikchakraborty200

## 🧠 Skills Demonstrated
- Enumeration (Nmap, OSINT)
- Exploitation (Web vulnerabilities, misconfigurations)
- Privilege Escalation (Linux/Windows)
- Tools: Burp Suite, Metasploit, Nmap



System

Problem Statement
Create a C# Console Application to manage books in a small library. The librarian should be able to add books, search for a book, display all books, and delete a book with proper validations and exception handling.
Write the complete solution inside the Program.cs file.
 
Requirements
Class: Library
Create a class called Library.
Properties
List<string> bookList
Used to store book names in the library.
const int TotalBooks = 5;
Used to set the maximum number of books allowed in the library.
 
Methods
1. AddBook(string bookName)
This method should add a book to the bookList.
Validations
1.	Book name should not be null, empty, or whitespace. 
If invalid, throw:
ArgumentException
Message:
Book name cannot be null, empty or whitespace
2.	Total books should not be more than TotalBooks. 
If the limit is exceeded, throw:
InvalidOperationException
Message:
Cannot add more than 5 books
 
2. ShowAllBooks()
Display all books available in the library.
If no books are available, display:
No books available in the library
 
3. FindBook(string bookName)
Search for a book from the library.
If found, display:
Book Found: <bookName>
Otherwise, display:
Book Not Found
 
4. DeleteBook(string bookName)
Delete the given book from the library.
If book exists, delete and display:
Book deleted successfully
Otherwise, display:
Book not found, cannot delete
 
Program Class Requirements
In the Main method:
1.	Prompt the user to enter a comma-separated list of book names. 
2.	Add each book to the library using AddBook(). 
3.	Handle all exceptions using try-catch. 
4.	Prompt the user to enter a book name to search. 
5.	Call FindBook(). 
6.	Prompt the user to enter a book name to delete. 
7.	Call DeleteBook(). 
8.	Finally display all books using ShowAllBooks(). 
 
Input Format
A single line containing comma-separated book names
A second line containing the book name to search
A third line containing the book name to delete
 
Sample Input
CSharp Basics,SQL Server,ASP.NET Core,Angular Guide
SQL Server
Angular Guide
 
Expected Output
Book added successfully: CSharp Basics
Book added successfully: SQL Server
Book added successfully: ASP.NET Core
Book added successfully: Angular Guide

Book Found: SQL Server

Book deleted successfully

All Books:
CSharp Basics
SQL Server
ASP.NET Core
 
Constraints
Use List<string> Property
Use const int TotalBooks = 5
Use ArgumentException for invalid book name
Use InvalidOperationException for exceeding book limit
Use try-catch for exception handling
Use menu is not required
Write all code inside Program.cs

```csharp

// Import required namespace for basic input/output operations
using System;

// Import namespace for using List collection
using System.Collections.Generic;

// Library class to manage books
class Library
{
    // List to store all book names
    public List<string> bookList = new List<string>();

    // Maximum number of books allowed in library
    public const int TotalBooks = 5;

    // Method to add a book into the library
    public void AddBook(string bookName)
    {
        // Check if book name is null, empty, or contains only spaces
        if (string.IsNullOrWhiteSpace(bookName))
        {
            // Throw exception if book name is invalid
            throw new ArgumentException("Book name cannot be null, empty or whitespace");
        }

        // Check if maximum book limit has been reached
        if (bookList.Count >= TotalBooks)
        {
            // Throw exception if more than 5 books are added
            throw new InvalidOperationException("Cannot add more than 5 books");
        }

        // Add the book to the list after removing extra spaces
        bookList.Add(bookName.Trim());

        // Display success message
        Console.WriteLine($"Book added successfully: {bookName.Trim()}");
    }

    // Method to display all books
    public void ShowAllBooks()
    {
        // Check if library has no books
        if (bookList.Count == 0)
        {
            // Display message if library is empty
            Console.WriteLine("No books available in the library");

            // Exit method
            return;
        }

        // Display heading
        Console.WriteLine("All Books:");

        // Loop through each book in the list
        foreach (string book in bookList)
        {
            // Display current book name
            Console.WriteLine(book);
        }
    }

    // Method to search for a book
    public void FindBook(string bookName)
    {
        // Check if the book exists in the list
        if (bookList.Contains(bookName))
        {
            // Display found message
            Console.WriteLine($"Book Found: {bookName}");
        }
        else
        {
            // Display not found message
            Console.WriteLine("Book Not Found");
        }
    }

    // Method to delete a book
    public void DeleteBook(string bookName)
    {
        // Remove() returns true if book is found and deleted
        if (bookList.Remove(bookName))
        {
            // Display success message
            Console.WriteLine("Book deleted successfully");
        }
        else
        {
            // Display message if book does not exist
            Console.WriteLine("Book not found, cannot delete");
        }
    }
}

// Main program class
class Program
{
    // Starting point of the application
    static void Main(string[] args)
    {
        // Create object of Library class
        Library library = new Library();

        // Read comma-separated book names from user
        string inputBooks = Console.ReadLine();

        // Read book name to search
        string searchBook = Console.ReadLine();

        // Read book name to delete
        string deleteBook = Console.ReadLine();

        // Split input string into array using comma separator
        string[] books = inputBooks.Split(',');

        // Loop through each book name
        foreach (string book in books)
        {
            try
            {
                // Add book to library after removing extra spaces
                library.AddBook(book.Trim());
            }
            catch (Exception ex)
            {
                // Display exception message if error occurs
                Console.WriteLine(ex.Message);
            }
        }

        // Print blank line
        Console.WriteLine();

        // Search for the required book
        library.FindBook(searchBook);

        // Print blank line
        Console.WriteLine();

        // Delete the required book
        library.DeleteBook(deleteBook);

        // Print blank line
        Console.WriteLine();

        // Display all remaining books
        library.ShowAllBooks();
    }
}
```

