---
title: "Database Connectivity Prepared Statement"
date: 2025-05-08T22:27:07+05:30
draft: false
tags: ["Java", "JDBC", "PreparedStatement", "SQL", "OOP"]
categories: ["OOPs"]
---

## Prepared Statement

A **PreparedStatement** is an interface in JDBC that allows you to execute SQL queries more securely and efficiently. It is used to execute parameterized SQL queries, preventing **SQL injection** and improving performance, especially when executing the same query multiple times with different parameters.

---

### Benefits of Prepared Statements

1. **Prevents SQL Injection**: 
   - Prepared statements automatically escape user input, protecting against SQL injection attacks.
2. **Efficiency**: 
   - SQL queries are precompiled, making repeated executions faster.
3. **Security**: 
   - No need to manually handle input sanitization.

---

### Creating and Using a Prepared Statement

1. **Create a PreparedStatement**  
   Use `Connection.prepareStatement()` to create a prepared statement.

   ```java
   String sql = "INSERT INTO users (name, age) VALUES (?, ?)";
   PreparedStatement pstmt = conn.prepareStatement(sql);
````

2. **Set Parameters**
   Use `setXXX()` methods to bind values to the placeholders (`?`).

   ```java
   pstmt.setString(1, "John Doe");
   pstmt.setInt(2, 30);
   ```

3. **Execute the Query**
   Use `executeUpdate()` for INSERT, UPDATE, or DELETE queries.

   ```java
   pstmt.executeUpdate();
   ```

4. **Close Resources**
   Always close the `PreparedStatement` and `Connection` to avoid resource leaks.

   ```java
   pstmt.close();
   conn.close();
   ```

---

### Example: Using PreparedStatement to Insert Data

```java
import java.sql.*;

public class PreparedStatementExample {
    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");

            String sql = "INSERT INTO users (name, age) VALUES (?, ?)";
            PreparedStatement pstmt = conn.prepareStatement(sql);
            pstmt.setString(1, "Alice");
            pstmt.setInt(2, 25);
            pstmt.executeUpdate();

            System.out.println("Data inserted successfully!");

            pstmt.close();
            conn.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

### 🔗 Related Notes

* [Database Connectivity]({{< ref "posts/oops/database-connectivity.md" >}})
* [CallableStatement]({{< ref "posts/oops/database-connectivity-callable-statement.md" >}})
* [ResultSet]({{< ref "posts/oops/resultset.md" >}})
