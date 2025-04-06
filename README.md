# gravity_book Database – My First SQL Learning Experience

Hi all,

I am here to narrate a short story about the **"gravity_book"** database, which is my first database to explore and practice with, as I am new to SQL. To make it easier for me to understand and explain, I have narrated this as a story.

I took this database from the following link:  
[https://github.com/bbrumm/databasestar/tree/main/sample_databases](https://github.com/bbrumm/databasestar/tree/main/sample_databases)

## My Initial Question

As a beginner, I had a very basic question:

> Why do we create multiple tables and connect them using primary keys and foreign keys when we already have all the information available and could just put everything into a single table?

Later, I realized that using multiple related tables helps to avoid redundancy, maintain consistency, and make the database more efficient and flexible. This concept is known as **normalization**, and it plays a vital role in organizing and managing data effectively.

## Tables in the Database

The database contains several tables:

author, publisher, book_language, book, book_author, address_status, address, customer, customer_address, shipping_method, cust_order, order_status, order_line, order_history


Here, I am going to share my understanding of the **first five tables** so that by the end of this explanation, you will have a better idea of how the remaining tables are related as well.

---

### Authors

The `author` table contains:

- `author_id` (Primary Key) – must always be **unique** and **not null**
- `author_name` – no constraint; multiple authors can share the same name

Each author is assigned a unique `author_id`, even if two authors have the same name. This ensures the system can always identify exactly who wrote what, with zero confusion.

> `author_id` is the one true identifier for an author – unique and never empty.

---

### Publishers

The `publisher` table contains:

- `publisher_id` (Primary Key)
- `publisher_name`

There are many publishing houses, both big and small. Each one has a unique `publisher_id`. For example, whether it is "Penguin Books" or "Tiny Tales Press", each is listed with its own ID. When a book is published, it simply refers to the publisher’s ID.

---

### Book Language

The `book_language` table includes:

- `language_id` (Primary Key)
- `language_code`
- `language_name`

Books are written in different languages. Each language is identified by a unique `language_id`, along with its code (like `EN`, `ES`) and name. Multiple books can reference the same language by using this ID.

---

### Books

The `book` table includes:

- `book_id` (Primary Key)
- `title`
- `isbn13`
- `language_id` (Foreign Key → `book_language.language_id`)
- `num_pages`
- `publication_date`
- `publisher_id` (Foreign Key → `publisher.publisher_id`)

Each book has a unique ID, along with its own details. It also references the language and publisher using foreign keys, which avoids repeating information.

---

### Book Author

The `book_author` table contains:

- `book_id` (Foreign Key → `book.book_id`)
- `author_id` (Foreign Key → `author.author_id`)

These two fields together form a **composite primary key**.

This table handles the many-to-many relationship between books and authors:

- A book may have multiple authors
- An author may have written multiple books
- Each author-book pair is stored as a unique row

If a book has three authors, there will be three rows in the `book_author` table – same `book_id`, different `author_id`s. No duplicate pair is allowed.

---

## Conclusion

In the world of the `gravity_book` database:

- Authors are uniquely identified and can write multiple books  
- Publishers can publish many books  
- Languages are reused across books  
- Books tie everything together with one language, one publisher, and possibly many authors  
- The `book_author` table acts as a bridge connecting books to authors in a clean, structured way

By using primary keys and foreign keys, the database remains organized, consistent, and easy to maintain—even as the data grows.

---

I hope this explanation provides a clear understanding of how these tables are connected and why relational databases are designed this way.

You are always welcome to correct me if I have made any mistakes in my explanation. I am here to learn, improve, and grow.

**Thank you.**


