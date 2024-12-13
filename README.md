# MongoDB CRUD Operations Task
This repository demonstrates MongoDB CRUD (Create, Read, Update, Delete) operations using the MongoDB shell. The task is aimed at practicing essential database operations and building a deeper understanding of MongoDB commands.

# Description
The project uses a "library" database containing a "books" collection. The collection includes information about books, such as their title, author, published year, and genre. The following operations are performed:

1. Create Operation
Create a new database: library
Create a collection: books
Insert a document with details of a book.
2. Read Operation
Retrieve all documents.
Find documents matching specific criteria (e.g., author is "J.K. Rowling").
Fetch the document with the earliest published year.
3. Update Operation
Update the published year of a specific book.
Add a new field genre to all documents.
4. Delete Operation
Remove a specific book by title.
Delete all books published before a certain year.
5. Advanced Query
Retrieve the top 3 recently published books.
Search for books where the title contains "MongoDB".

# Prerequisites
MongoDB installed and running.
Access to MongoDB shell (mongosh) or a client like MongoDB Compass.

# Queries Used
1. Create Operation
// Switch to the database named "library" (it will be created if it doesn't exist)

use library

// Create the "books" collection and insert a document
// with fields: title, author, and published_year

db.books.insertOne({
    title: "To Kill a Mockingbird",
    author: "Harper Lee",
    published_year: 1960
})

2. Read Operation
// Retrieve all documents from the "books" collection

db.books.find()

// Find and display only the documents where the author is "J.K. Rowling"

db.books.find({ author: "J.K. Rowling" })

// Fetch and display the document with the earliest published year

db.books.find().sort({ published_year: 1 }).limit(1)

3. Update Operation
// Update the published year of the book with the title "The Catcher in the Rye" to the current year

db.books.updateOne(
    { title: "The Catcher in the Rye" },
    { $set: { published_year: 2015 } }
)

// Add a new field "genre" with the value "Mystery" to all documents in the "books" collection

db.books.updateMany(
    {},
    { $set: { genre: "Mystery" } }
)

4. Delete Operation
// Remove the document with the title "1984" from the "books" collection

db.books.deleteOne({ title: "1984" });

// Delete all documents from the "books" collection where the published year is before 2000

db.books.deleteMany({ published_year: { $lt: 2000 } });

5. Advanced Query
// Find and display the top 3 recently published books from the "books" collection

db.books.find().sort({ published_year: -1 }).limit(3)

// Retrieve documents from the "books" collection where the title contains the word "MongoDB"

db.books.find({ title: /MongoDB/i })

