# Cheat Sheet

- **H2:** Provides an in-memory relational database (for prototyping / development purposes).

- **MySQL / PostgreSQL:** Relational database management system used in production environments (covered in the deployment section).


- **Spring Boot JPA:** Allows a Spring Boot application to interact with an SQL database.

- **CRUD Repository**: Provides methods that can Create, Read, Update, or Delete records.
- **Entity**: Java object that Spring Boot JPA can manage.

- **`@Table`**: Specifies the table for the annotated entity.
   - `name`: Name of the table.
   - `uniqueConstraints`: Unique constraints to be placed on the table.

- **`@Column`**: Maps a field to a table column.
  - `name`: Name of column.
  - `nullable`: Boolean that determines if the column can accept nulls.
  - `unique`: Boolean that determines if the column rejects duplicates.

- **Primary Key**: Column that uniquely identifies each record inside a table.
  - `@Id`: Applied on a field that maps to a primary key.
- **Foreign Key**: References the primary key of another table.
  - When applicable, put the foreign key column in the table that cannot live without the other.
  - `@JoinColumn`: Specifies a column for joining an entity association.
      - `name`: Name of the column.
     - `referencedColumnName`: Name of the column referenced by the foreign key column.
- **`@ManyToOne`**: Many rows in the child table belong to one row in the parent table.
- **`@OneToMany`**: One row in the parent table associates with many rows in the child table.




--------
##### Subscribe to our [YouTube Channel](https://www.youtube.com/@RayanSlim087?sub_confirmation=1) and Discover More Valuable Content!