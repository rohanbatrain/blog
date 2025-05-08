---
title: "Database Connectivity Callable Statement"
date: 2025-05-08T22:28:18+05:30
draft: false
tags: ["Java", "JDBC", "CallableStatement", "SQL", "OOP"]
categories: ["OOPs"]
---

## CallableStatement

A **CallableStatement** is an interface in JDBC that allows you to execute stored procedures and functions in a database. Unlike a `PreparedStatement`, which is used for executing SQL queries, a `CallableStatement` can execute database stored procedures or functions that may involve complex logic and multiple SQL statements.

---

### Benefits of CallableStatement

1. **Execute Stored Procedures**: 
   - Used to call stored procedures in the database, which are precompiled and can perform complex operations.
2. **Better Performance**: 
   - Stored procedures are compiled once and can be reused, improving execution speed.
3. **Return Multiple Results**: 
   - Callable statements can return multiple results, including output parameters.

---

### Creating and Using a CallableStatement

1. **Create a CallableStatement**  
   Use `Connection.prepareCall()` to create a callable statement.

   ```java
   String sql = "{call getUserDetails(?, ?)}";
   CallableStatement cstmt = conn.prepareCall(sql);
````

2. **Set Input Parameters**
   Use `setXXX()` methods to pass values to input parameters of the stored procedure.

   ```java
   cstmt.setInt(1, 101);  // Set user ID
   ```

3. **Register Output Parameters**
   Use `registerOutParameter()` to specify output parameters.

   ```java
   cstmt.registerOutParameter(2, Types.VARCHAR);  // Register output parameter for name
   ```

4. **Execute the Procedure**
   Use `execute()` to call the stored procedure.

   ```java
   cstmt.execute();
   ```

5. **Retrieve Output Parameters**
   Use `getXXX()` methods to get the result of output parameters.

   ```java
   String name = cstmt.getString(2);  // Get the user name from the output
   ```

6. **Close Resources**
   Always close the `CallableStatement` and `Connection` to release resources.

   ```java
   cstmt.close();
   conn.close();
   ```

---

### Example: Using CallableStatement to Call a Stored Procedure

```java
import java.sql.*;

public class CallableStatementExample {
    public static void main(String[] args) {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");

            // Calling a stored procedure
            String sql = "{call getUserDetails(?, ?)}";
            CallableStatement cstmt = conn.prepareCall(sql);

            // Setting input parameter
            cstmt.setInt(1, 101);  // User ID

            // Registering output parameter
            cstmt.registerOutParameter(2, Types.VARCHAR);

            // Executing the stored procedure
            cstmt.execute();

            // Retrieving the output parameter
            String name = cstmt.getString(2);
            System.out.println("User Name: " + name);

            cstmt.close();
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
* [PreparedStatement]({{< ref "posts/oops/database-connectivity-prepared-statement.md" >}})
* [ResultSet]({{< ref "posts/oops/resultset.md" >}})

