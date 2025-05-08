---
title: "Database Connectivity"
date: 2025-05-08T22:25:01+05:30
draft: false
tags: ["Java", "Database", "JDBC", "OOP", "SQL"]
categories: ["OOPs"]
---

## Database Connectivity

In Java, **JDBC (Java Database Connectivity)** provides an API for connecting to relational databases, executing SQL queries, and processing results. It enables Java applications to interact with databases like MySQL, Oracle, PostgreSQL, and others.

---

### Steps to Connect to a Database

1. **Load the Database Driver**  
   You need to load the database-specific driver class using `Class.forName()`.

   ```java
   Class.forName("com.mysql.cj.jdbc.Driver");
```

2. **Establish a Connection**
   Use the `DriverManager.getConnection()` method to establish a connection.

   ```java
   Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "user", "password");
   ```

3. **Create a Statement**
   Create a `Statement` object to execute SQL queries.

   ```java
   Statement stmt = conn.createStatement();
   ```

4. **Execute Queries**
   Use `executeQuery()` for SELECT queries and `executeUpdate()` for INSERT, UPDATE, DELETE.

   ```java
   ResultSet rs = stmt.executeQuery("SELECT * FROM users");
   ```

5. **Process Results**
   Iterate over the `ResultSet` to process the data.

   ```java
   while (rs.next()) {
       System.out.println(rs.getString("name"));
   }
   ```

6. **Close Connections**
   Close the `ResultSet`, `Statement`, and `Connection` to release resources.

   ```java
   rs.close();
   stmt.close();
   conn.close();
   ```

---

### Example Code for Database Connectivity

```java
import java.sql.*;

public class DatabaseExample {
    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");
            Statement stmt = conn.createStatement();
            ResultSet rs = stmt.executeQuery("SELECT * FROM users");

            while (rs.next()) {
                System.out.println("ID: " + rs.getInt("id") + ", Name: " + rs.getString("name"));
            }

            rs.close();
            stmt.close();
            conn.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

### 🔗 Related Notes

* [Generic Class]({{< ref "posts/oops/generic-class.md" >}})
* [Lambdas]({{< ref "posts/oops/lambdas.md" >}})
* [Database Connectivity - Prepared Statement]({{< ref "posts/oops/database-connectivity-prepared-statement.md" >}})
