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
