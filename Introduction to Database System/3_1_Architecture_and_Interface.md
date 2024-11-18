# 1. ER & Relational Models
- **RDBMS Definition**
  - A database management system that supports the relational model.
- **Architecture Origin**
  - Influenced by IBM System R (announced in 1974).
- **VanillaDB Project**
  - **VanillaCore**: A standalone RDBMS implemented in Java.
  - **VanillaBench**: Common benchmarking tools for RDBMS.
  - **VanillaComm**: Communication infrastructure for distributed RDBMS.
![alt text](pic/3-1/3-1-1.png)
![alt text](pic/3-1/3-1-2.png)
# 2. Reducing Redundancy & Inconsistency
- **Functional Architecture**
  - Query Engine.
  - Storage Engine.
  - Supported interfaces: SQL, JDBC, Native Query, and Storage Interface.
- **SQL Support**
  - Supports a subset of SQL-92, including basic DDL and DML operations.
  - Limitations include no support for JOIN, NULL values, or complex expressions.
- **Data Storage and Access**
  - Database: Directory.
  - Table: File.
  - Record: Bytes (accessed via pages).
![alt text](pic/3-1/3-1-3.png)
# 3. Practical Applications
- **JDBC Usage Example**
  - **Connect to Database**:
    ```java
    Driver d = new JdbcDriver();
    Connection conn = d.connect("jdbc:vanilladb://localhost", null);
    ```
  - **Execute Query**:
    ```java
    Statement stmt = conn.createStatement();
    String qry = "SELECT s-name, d-name FROM departments, students WHERE major-id = d-id";
    ResultSet rs = stmt.executeQuery(qry);
    ```
  - **Output Results**:
    ```java
    while (rs.next()) {
        String sName = rs.getString("s-name");
        String dName = rs.getString("d-name");
        System.out.println(sName + "\t" + dName);
    }
    ```

# 4. Architecture of VanillaCore
- **Interfaces**:
  - SQL.
  - JDBC.
  - Native Query Interface.
  - Storage Interface.
- **Components**:
  - Server infrastructure (e.g., JDBC, SQL, Tx).
  - Query Engine.
  - Storage Engine.

# 5. Metadata Management
- **Types of Metadata**
  - Table Metadata: Includes schema, field types, and offsets.
  - View Metadata: Properties of views (definition, creator).
  - Index Metadata: Indexes on fields.
  - Statistical Metadata: Data for query cost estimation.
- **Storage of Metadata**
  - Stored in catalog tables (`tblcat.tbl`, `fldcat.tbl`, `idxcat.tbl`, `viewcat.tbl`).
  - Statistical metadata is kept in memory and periodically updated for fast access.

# 6. Storage Interface
- **File Structure**
  - Data organized into blocks (smallest OS I/O unit).
  - Blocks loaded into memory pages for processing.
- **RecordFile API**
  - Provides random and sequential access to records.
  - Example Methods:
    ```java
    RecordFile.moveToRecordId(recordId);
    RecordFile.getVal(fieldName);
    RecordFile.setVal(fieldName, value);
    RecordFile.insert();
    RecordFile.delete();
    ```

# 7. Assigned Readings
- **References**
  - System R: "Relational Approach to Database Management," ACM Transactions on Database Systems, 1976.
  - "Architecture of a Database System," Foundations and Trends in Databases, 2007.
  - Edward Sciore, "Database Design and Implementation," 2008.

# 8. Assignment
- Implement a JDBC client using stored procedures.
- Compare performance using provided data population and benchmarking tools.
