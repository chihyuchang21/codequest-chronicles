# 1. ER & Relational Models
- **Weak Entities**
  - Entities dependent on a strong entity for their existence.
- **Inheritance**
  - Subclass entities inherit attributes and relationships from their parent class.

# 2. Reducing Redundancy & Inconsistency
- **Functional Dependencies**
  - A relationship where one attribute (or a set of attributes) uniquely determines another attribute.
- **Normal Forms**
  - Structured forms to reduce redundancies and dependencies, including 1st, 2nd, 3rd, and BCNF (Boyce-Codd Normal Form).

# 3. Practical Applications
- **Modeling User Addresses**
  - Handling multiple addresses per user and ensuring addresses are deleted when users are deleted using CASCADE in SQL.
- **SQL Example**:
    - ```sql
      CREATE TABLE addresses (
        userId serial NOT NULL,
        type text NOT NULL,
        PRIMARY KEY (userId, type),
        FOREIGN KEY userId REFERENCES users ON DELETE CASCADE
      );
      ```

# 4. Anomalies in Data
- **Types of Anomalies**:
    - **Insertion Anomaly**: Difficulty in adding data due to missing information.
    - **Update Anomaly**: Inconsistencies that arise when multiple instances of data are not updated together.
    - **Deletion Anomaly**: Loss of useful data due to deletion of other data.

# 5. Normalization Process
- **Purpose**: Ensuring data within the database is free of duplication and inconsistencies.
- **Forms Explained**:
    - **1st Normal Form**: Eliminates multi-valued attributes.
    - **2nd Normal Form**: Ensures all non-key attributes are fully functional dependent on the primary key.
    - **3rd Normal Form**: Ensures all fields can be derived only from the primary key and not other non-prime attributes.
    - **BCNF**: A stronger version of 3rd normal form where every determinant is a candidate key.

# 6. Functional Dependencies and Normal Forms
- **Functional Dependency**: A relationship where a value of one attribute (or a set of attributes) uniquely determines another attribute.
- **Challenges with Normal Forms**: While reducing redundancy and enhancing data integrity, they can increase query complexity due to multiple joins.

# 7. Assigned Reading
- **Focus**: Chapters on ER & relational models, Functional Dependencies, and normal forms to deepen understanding of data structuring.
