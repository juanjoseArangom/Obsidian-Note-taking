The **Entity-Relationship (ER) Model** is a high-level conceptual data model used to define the data elements and relationships in a system. It provides a graphical way to design a database structure before it's implemented in a relational database.

---

## 📘 Key Concepts

### 1. **Entity**
- An entity is a "thing" or "object" in the real world with an independent existence.
- **Example:** `Student`, `Course`, `Employee`

Entities are represented as **rectangles** in ER diagrams.

### 2. **Entity Set**
- A collection of similar types of entities.
- **Example:** The set of all students enrolled in a university.

### 3. **Attributes**
- Characteristics or properties of an entity.
- **Example:** For a `Student` entity, attributes could be `StudentID`, `Name`, `Email`.

Attributes are shown as **ellipses** connected to their entities.

#### Types of Attributes:
- **Simple (Atomic):** Cannot be divided further (`Age`, `Name`)
- **Composite:** Can be divided into sub-parts (`FullName` into `FirstName`, `LastName`)
- **Derived:** Can be calculated from other attributes (`Age` from `DateOfBirth`)
- **Multivalued:** Can have multiple values (`PhoneNumbers`)

### 4. **Primary Key**
- An attribute (or set of attributes) that uniquely identifies an entity.

---

## 🔗 Relationships

### 1. **Relationship**
- A relationship is an association among entities.
- **Example:** `Enrolled` between `Student` and `Course`

Relationships are represented by **diamonds** in ER diagrams.

### 2. **Relationship Set**
- A collection of relationships of the same type.

### 3. **Degree of a Relationship**
- Number of entity sets involved:
  - **Unary (1-ary):** Involves one entity set (e.g., `manages` between Employees)
  - **Binary (2-ary):** Involves two entity sets (most common)
  - **Ternary (3-ary):** Involves three entity sets

### 4. **Cardinality (Multiplicity)**
- Defines the number of instances of one entity related to the number of instances of another:
  - **One-to-One (1:1)**
  - **One-to-Many (1:N)**
  - **Many-to-Many (M:N)**

### 5. **Participation Constraints**
- **Total Participation:** Every instance of the entity is involved in the relationship (shown with double line).
- **Partial Participation:** Some instances may not be involved (shown with single line).

---

## 🧬 Example: University Database

```text
Entities:
- Student (StudentID, Name, Email)
- Course (CourseID, Title, Credits)

Relationship:
- Enrolled (Student, Course, Grade)

Cardinality:
- A Student can enroll in many Courses (1:N)
- A Course can have many Students (M:N)
```


