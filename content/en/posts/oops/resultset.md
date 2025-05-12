---
title: "Resultset"
date: 2025-05-08T22:35:23+05:30
draft: false
tags: ["Java", "JDBC", "ResultSet", "SQL", "OOP"]
categories: ["OOPs"]
---

## ResultSet

In JDBC, the **ResultSet** interface represents the result set of a query. It provides methods to read data returned by a query, typically from a `SELECT` statement. A `ResultSet` is created by executing a query using the `Statement` or `PreparedStatement` objects, and it allows navigation and extraction of data from the result.

---

### Types of ResultSet

1. **Forward-only**: 
   - This is the default type, where you can only move the cursor forward through the result set.
   - Created with: `Statement statement = conn.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_READ_ONLY);`
   
2. **Scrollable**: 
   - Allows navigation in both directions, forward and backward, through the result set.
   - Created with: `Statement statement = conn.createStatement(ResultSet.TYPE_SCROLL_INSENSITIVE, ResultSet.CONCUR_READ_ONLY);`
   
3. **Updatable**: 
   - Allows updating the values in the result set.
   - Created with: `Statement statement = conn.createStatement(ResultSet.TYPE_SCROLL_INSENSITIVE, ResultSet.CONCUR_UPDATABLE);`

---

### Common Methods of ResultSet

- **next()**: Moves the cursor to the next row in the result set.
  
  ```java
  while (rs.next()) {
      System.out.println(rs.getString("name"));
  }
```

* **getString()**: Retrieves a column value as a `String`.

  ```java
  String name = rs.getString("name");
  ```

* **getInt()**: Retrieves a column value as an `int`.

  ```java
  int id = rs.getInt("id");
  ```

* **getBoolean()**: Retrieves a column value as a `boolean`.

  ```java
  boolean isActive = rs.getBoolean("is_active");
  ```

* **getDate()**: Retrieves a column value as a `Date`.

  ```java
  Date birthDate = rs.getDate("birth_date");
  ```

---

### Example: Using ResultSet to Process Query Results

```java
import java.sql.*;

public class ResultSetExample {
    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");
            Statement stmt = conn.createStatement();
            ResultSet rs = stmt.executeQuery("SELECT id, name, age FROM users");

            while (rs.next()) {
                int id = rs.getInt("id");
                String name = rs.getString("name");
                int age = rs.getInt("age");
                System.out.println("ID: " + id + ", Name: " + name + ", Age: " + age);
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

* [CallableStatement]({{< ref "en/posts/oops/database-connectivity-callable-statement.md" >}})
* [PreparedStatement]({{< ref "en/posts/oops/database-connectivity-prepared-statement.md" >}})
* [Database Connectivity]({{< ref "en/posts/oops/database-connectivity.md" >}})
