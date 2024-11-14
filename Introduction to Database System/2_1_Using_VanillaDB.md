# 1. VanillaDB Projects
- **VanillaCore**
  - A single-node Database Management System (DBMS) in VanillaDB.
- **VanillaBench**
  - A benchmarking tool to measure VanillaDB's performance.
- **VanillaComm**
  - Communication module designed for distributed DBMSs.

# 2. Setting Up the Environment
- **JDK 8**
  - Required to run VanillaDB.
  - [Download JDK 8 here](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).
- **Eclipse**
  - Recommended IDE for development with VanillaDB.
  - [Download Eclipse here](https://www.eclipse.org/downloads/packages/installer).

# 3. Downloading and Importing VanillaDB
- **Cloning the Project**
  - Clone VanillaDB from the repository: [VanillaDB repository](https://shwu10.cs.nthu.edu.tw/courses/databases/2020-spring/vanilladb).
- **Importing VanillaCore**
  - Choose a workspace directory in Eclipse (avoid directories containing `pom.xml`).
  - Select the cloned directory containing `pom.xml` to import VanillaCore.

# 4. Configuring VanillaCore Properties
- **vanilladb.properties**
  - Configuration file where all VanillaCore settings are stored.
  - Default directory for database files is the user directory if unspecified.

# 5. Starting VanillaCore
- **Arguments Required**
  - Specify the **Database Directory Name** and **properties file locations** to start the VanillaCore server.

# 6. Setting Up Run Configuration
- **Steps**:
  - Right-click to create a new configuration in Eclipse.
  - Name the configuration and select the current project.
  - **Arguments**:
    - **Program Arguments**:
      - `[Database Directory Name]`, e.g., `student-db`.
    - **VM Arguments**:
      ```bash
      -Dorg.vanilladb.core.config.file=target/classes/org/vanilladb/core/vanilladb.properties
      -Djava.util.logging.config.file=target/classes/java/util/logging/logging.properties
      ```
  - Click **Apply** and **Run**.

# 7. Server Messages
- **Expected Output**:
  - No errors indicate the server setup is correct.
- **Warning and Error Messages**:
  - “error reading config file, using default” - Incorrect properties file path.
  - “can’t find property: …., using default: …” - Missing properties in the configuration file.

# 8. Using the Console SQL Interpreter
- **Steps**:
  - Create a new run configuration and name it.
  - Choose **ConsoleSQLInterpreter** as the **Main Class**.
  - No VM arguments are required.
  - Run the configuration to start the Console SQL Interpreter.

# 9. Additional Resources
- **SQL Query Documentation**:
  - [VanillaDB SQL documentation](https://shwu10.cs.nthu.edu.tw/courses/databases/2020-spring/faq/blob/master/Vanilladb_Sql.md)
- **FAQ and Support**:
  - [VanillaDB FAQ](https://shwu10.cs.nthu.edu.tw/courses/databases/2020-spring/faq)

