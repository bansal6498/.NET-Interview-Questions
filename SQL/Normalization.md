## Normalization
Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves dividing large tables into smaller ones and defining relationships between them.
There are several normal forms (1NF, 2NF, 3NF, BCNF, etc.), with each having a set of rules to achieve higher levels of normalization.
-   **1NF** (First Normal Form): Ensures that the table contains only atomic (indivisible) values and each record is unique.
-   **2NF** (Second Normal Form): Achieved when a table is in 1NF and all non-key attributes are fully dependent on the primary key.
-   **3NF** (Third Normal Form): Achieved when a table is in 2NF and all attributes are functionally dependent only on the primary key.