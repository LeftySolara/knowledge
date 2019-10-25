# Database Normalization

Normalization is the process of structuring a relational database in accordance with a series of "normal forms". This is to reduce data redundancy and improve data integrity.

## Objectives

The objectives of normalization beyond First Normal Form are as follows:
1) Remove undesirable insertion, update, and deletion dependencies.
2) Reduce the need for restructuring the collection of relations when new types of data are introduced.
3) Make the relational model more informative to users.
4) Make the collection of relations neutral to the query statistics, where these stats are liable to change as time goes by.

A fully normalized database allows its structure to be extended to accomodate new types of data without changing existing structure too much.

Note that normal forms beyond 4NF are purely of academic interest; the problems they exist to solve rarely occur in practice.

### Side-Effects in Non-Normalized Databases

- Update Anomalies
    - The same information can be expressed on multiple rows, so updates may result in logical inconsistencies.
    - Example: an employee having two different addresses listed because there are multiple records for them.
- Insertion Anomalies
    - When certain facts cannot be recorded at all.
    - Example: Not being able to add a new faculty member who hasn't been assigned a course yet.
- Deletion Anomalies
    - Deletion of data representing certain facts necessitates the deletion of data representing different facts.
    - Example: If a faculty member temporary ceases to be assigned to any courses, we must delete all the records where they appear, effectively deleting the faculty member.

## Links
- [Wikipedia: Database Normalization](https://en.wikipedia.org/wiki/Database_normalization#Objectives)