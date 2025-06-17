# Week 8 – Database Integration (JDBC + SQL CRUD)

---

## Why Learn This?

Nearly every real-world application needs to store and retrieve data. This week you'll learn to:

* Connect Java programs to relational databases using JDBC.
* Write SQL queries from Java.
* Perform Create, Read, Update, and Delete (CRUD) operations.
  These skills are fundamental for full-stack development, enterprise applications, and backend engineering.

---

## Week 8 Concepts & Notes

### JDBC (Java Database Connectivity)

JDBC is a Java API for connecting and executing SQL commands with databases.

---

### Steps for JDBC Connection

1. **Load the Driver** (Optional for modern JDBC)
2. **Establish Connection**
3. **Create Statement**
4. **Execute SQL**
5. **Process Results**
6. **Close Resources**

---

### Sample: Connect to SQLite

```java
import java.sql.*;

public class ConnectDB {
    public static void main(String[] args) {
        try (Connection conn = DriverManager.getConnection("jdbc:sqlite:test.db")) {
            System.out.println("Connected!");
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

---

### Creating a Table

```java
try (Connection conn = DriverManager.getConnection("jdbc:sqlite:test.db")) {
    Statement stmt = conn.createStatement();
    String sql = "CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, name TEXT)";
    stmt.execute(sql);
}
```

---

### Inserting Data

```java
String sql = "INSERT INTO users (name) VALUES (?)";
PreparedStatement pstmt = conn.prepareStatement(sql);
pstmt.setString(1, "Alice");
pstmt.executeUpdate();
```

---

### Reading Data

```java
ResultSet rs = stmt.executeQuery("SELECT * FROM users");
while (rs.next()) {
    int id = rs.getInt("id");
    String name = rs.getString("name");
    System.out.println(id + " | " + name);
}
```

---

### Updating Data

```java
String sql = "UPDATE users SET name = ? WHERE id = ?";
PreparedStatement pstmt = conn.prepareStatement(sql);
pstmt.setString(1, "Bob");
pstmt.setInt(2, 1);
pstmt.executeUpdate();
```

---

### Deleting Data

```java
String sql = "DELETE FROM users WHERE id = ?";
PreparedStatement pstmt = conn.prepareStatement(sql);
pstmt.setInt(1, 1);
pstmt.executeUpdate();
```

---

## Quiz Questions

1. **What is JDBC used for?**

2. **Which object is used to execute SQL queries?**

3. **What is the benefit of using `PreparedStatement` over `Statement`?**

4. **What does `ResultSet` represent?**

5. **What method is used to connect to a database?**

6. **What SQL command deletes a record?**

---

## Coding Challenges

1. **Database Connection Test**
   Connect to a SQLite database named `week8.db` and print "Connected".

2. **Create Table**
   Create a table `products` with fields: `id`, `name`, `price`.

3. **Insert Product**
   Insert a product into the `products` table using `PreparedStatement`.

4. **Select Products**
   Write a method to retrieve and print all products from the database.

5. **Update Product Price**
   Update the price of a product given its ID.

6. **Delete Product**
   Delete a product from the database by ID.

---

## Week 8 Summary

* Connected Java apps to a relational database using JDBC.
* Created tables and used SQL for CRUD operations.
* Learned to use `PreparedStatement` to avoid SQL injection.
* Read and manipulated real-world data programmatically.

## For Next Week

### Reading 

* https://codingnomads.com/course/learn-sql-mysql-databases
    * Browse entire mmodule

* https://codingnomads.com/course/java-programming-301
    * Section 8) SQL & JDBC

### Assignments (in IntelliJ)

Complete the following exercises -- you can, of course, do them all:

* src/mysql/labs -> exercises 1-4