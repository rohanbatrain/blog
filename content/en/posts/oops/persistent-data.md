---
title: "Persistent Data"
date: 2025-05-08T22:37:39+05:30
draft: false
tags: ["Java", "JDBC", "Persistent Data", "SQL", "OOP"]
categories: ["OOPs"]
---

## Persistent Data

In Java and database management systems, **Persistent Data** refers to data that is stored in a way that it survives the program's termination and can be retrieved in future executions. This is typically achieved using a database where data is stored in tables and can be accessed through SQL queries. In the context of JDBC (Java Database Connectivity), persistent data is the data stored and retrieved from relational databases.

---

### Key Concepts of Persistent Data

1. **Database Storage**: 
   - Persistent data is stored in database tables, and each table consists of rows (records) and columns (fields). The database system ensures that the data remains intact even if the application is stopped.
   
2. **JDBC Connection**:
   - A connection is established to the database using the `Connection` object in JDBC, which allows you to perform CRUD (Create, Read, Update, Delete) operations on the persistent data.
   
3. **ResultSet for Query Results**:
   - The `ResultSet` object in JDBC allows you to retrieve data from the database and read through the results in a structured manner. The data fetched from a query is considered persistent data until it is removed or altered in the database.

4. **Transaction Management**:
   - **Transactions** in JDBC allow you to execute multiple SQL operations as a single unit. If any part of the transaction fails, the entire transaction can be rolled back to maintain the consistency of the persistent data.

---

### Example: Storing and Retrieving Persistent Data

Consider the example where we store user information in a database and retrieve it using JDBC:

```java
import java.sql.*;

public class PersistentDataExample {
    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");

            // Insert data into the database (Persistent data)
            String insertSQL = "INSERT INTO users (name, age) VALUES (?, ?)";
            PreparedStatement pstmt = conn.prepareStatement(insertSQL);
            pstmt.setString(1, "Bob");
            pstmt.setInt(2, 28);
            pstmt.executeUpdate();

            // Retrieve data from the database (Persistent data)
            String selectSQL = "SELECT name, age FROM users WHERE name=?";
            PreparedStatement selectStmt = conn.prepareStatement(selectSQL);
            selectStmt.setString(1, "Bob");
            ResultSet rs = selectStmt.executeQuery();

            while (rs.next()) {
                String name = rs.getString("name");
                int age = rs.getInt("age");
                System.out.println("Name: " + name + ", Age: " + age);
            }

            rs.close();
            pstmt.close();
            selectStmt.close();
            conn.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

This example demonstrates how persistent data (the user's name and age) is inserted into and retrieved from the database using JDBC.

---

### 🔗 Related Notes

* [Database Connectivity]({{< ref "en/posts/oops/database-connectivity.md" >}})
* [ResultSet]({{< ref "en/posts/oops/resultset.md" >}})
* [PreparedStatement]({{< ref "en/posts/oops/database-connectivity-prepared-statement.md" >}})
* [CallableStatement]({{< ref "en/posts/oops/database-connectivity-callable-statement.md" >}})
