## ➡️ Functional Dependencies

A functional dependency is a relationship between attributes in a table. It states that if you know the value of one attribute (or a set of attributes), you can determine the value of another attribute (or set of attributes). We represent a functional dependency as $A \rightarrow B$, meaning attribute A functionally determines attribute B.

**Concept:** Knowing one piece of information *tells you* another piece of information within the same row. There's a dependent relationship.

**Example:**

Consider a `📚 Books` table again:

* `ISBN`
* `📚 Title`
* `✍️ Author`
* `📅 PublicationYear`

Here are some functional dependencies that might exist:

* `ISBN` $\rightarrow$ `📚 Title` (If you know the ISBN, you know the book's title) 👉 ISBN ➡️ 📚
* `ISBN` $\rightarrow$ `✍️ Author` (If you know the ISBN, you know the author) 👉 ISBN ➡️ ✍️
* `ISBN` $\rightarrow$ `📅 PublicationYear` (If you know the ISBN, you know the publication year) 👉 ISBN ➡️ 📅
* `ISBN` $\rightarrow$ `📚 Title, ✍️ Author, 📅 PublicationYear` (Since ISBN determines each of the others individually, it determines them collectively) 👉 ISBN ➡️ 📚, ✍️, 📅

In a `🙋‍♀️ Students` table:

* `StudentID`
* `📧 Email`
* `🏠 Major`
* `🎂 DateOfBirth`

* `StudentID` $\rightarrow$ `📧 Email` 👉 StudentID ➡️ 📧
* `StudentID` $\rightarrow$ `🏠 Major` 👉 StudentID ➡️ 🏠
* `StudentID` $\rightarrow$ `🎂 DateOfBirth` 👉 StudentID ➡️ 🎂

Understanding functional dependencies is crucial for the process of normalization.

Let's clarify the concept of "complete functional dependence," which is more commonly referred to as **full functional dependency**. This is a crucial idea when you have keys made up of more than one attribute.

## ➡️ Full Functional Dependency (Complete Functional Dependence)

A full functional dependency is a type of functional dependency where an attribute (or set of attributes) is functionally dependent on a composite key, and **is not** functionally dependent on any proper subset of that composite key.

In simpler terms: if your key is made of multiple parts, a full functional dependency means that *all* parts of the key are needed to determine the other attribute. Knowing only *some* of the key parts isn't enough.

**Concept:** If attribute B depends on a composite key (A1, A2), it's a full functional dependency if B *cannot* be determined by A1 alone, or by A2 alone. You need the *combination* of A1 and A2.

**Example:**

Consider a table tracking the price of a specific product sold at a specific store on a given date. Let's call the table `🏪 DailyProductPrices`.

* `🏪 StoreID`
* `🍎 ProductID`
* `📅 PriceDate`
* `💰 Price`
* `📍 StoreLocation`

Let's assume the composite primary key for this table is (`🏪 StoreID`, `🍎 ProductID`, `📅 PriceDate`). This composite key uniquely identifies a specific product's price at a specific store on a specific day.

Now let's look at some functional dependencies:

1.  (`🏪 StoreID`, `🍎 ProductID`, `📅 PriceDate`) $\rightarrow$ `💰 Price`
    * This is a functional dependency because knowing the store, product, and date tells you the price.
    * Is it a *full* functional dependency? Yes, because you likely need all three parts of the key to determine the specific price on that day. The price of a product can vary by store and by date. 👉✅🔑➡️💰

2.  (`🏪 StoreID`, `🍎 ProductID`, `📅 PriceDate`) $\rightarrow$ `📍 StoreLocation`
    * This is also a functional dependency.
    * However, is it a *full* functional dependency? Probably not. The `📍 StoreLocation` likely only depends on the `🏪 StoreID`, not the `🍎 ProductID` or the `📅 PriceDate`. This is a **partial dependency**. 👉❌🔑➡️📍 (Partial Dependency on `🏪 StoreID`)

**Why is Full Functional Dependency Important?** 🤔

Full functional dependency is a core requirement for achieving **Second Normal Form (2NF)**. A table is in 2NF if it is in 1NF and all non-key attributes are fully functionally dependent on the primary key.

If a non-key attribute is only partially dependent on a composite primary key (like `📍 StoreLocation` depending only on `🏪 StoreID` in the example above), it indicates redundancy and potential update anomalies. To move to 2NF, you would typically remove the partially dependent attribute and the part of the key it depends on into a new table.

In our example, to normalize the `🏪 DailyProductPrices` table to 2NF, you would create a separate `🏪 Stores` table:

`🏪 Stores` table:

| StoreID | StoreLocation |
|---|---|
| 1 | Downtown |
| 2 | Uptown |

And the `🏪 DailyProductPrices` table would be updated to remove `📍 StoreLocation`:

`🏪 DailyProductPrices` table (in 2NF):

| StoreID | ProductID | PriceDate | Price |
|---|---|---|---|
| 1 | A1 | 2023-10-26 | 10 |
| 1 | B2 | 2023-10-26 | 15 |
| 2 | A1 | 2023-10-26 | 11 |

By ensuring full functional dependencies on the primary key (or any candidate key), you help eliminate partial dependencies and move towards a more normalized and robust database design. ✨

Let's delve into Armstrong's Axioms! These are a foundational set of inference rules used to deduce all the functional dependencies on a relational schema given a set of functional dependencies. Think of them as the fundamental laws that govern how functional dependencies behave.

## 📐 Armstrong's Axioms

Armstrong's Axioms are a set of sound and complete inference rules for functional dependencies.

* **Sound:** The rules do not generate any incorrect functional dependencies. If you derive a dependency using these axioms, it is guaranteed to be true if the original dependencies are true. ✅
* **Complete:** The rules can generate *all* functional dependencies that are logically implied by a given set of functional dependencies. You won't miss any valid dependencies. 💪

These axioms are essential for understanding the closure of a set of attributes (all the attributes that can be determined from that set) and for tasks like finding candidate keys and performing normalization.

There are three primary axioms:

### 1. Reflexivity (Inclusion) Axiom 🤔

If B is a subset of A, then A functionally determines B ($A \rightarrow B$). This is a bit of a self-evident rule – if you know a set of attributes, you trivially know any subset of those attributes.

**Concept:** If you have a group of facts, you automatically have any part of that group of facts.

**Formal Notation:** If $B \subseteq A$, then $A \rightarrow B$.

**Example:**

If you have the set of attributes {`📧 Email`, `📛 FirstName`}, you can determine the attribute `📧 Email`.

{`📧 Email`, `📛 FirstName`} $\rightarrow$ `📧 Email` 👉 {📧, 📛} ➡️ 📧

Similarly, {`📧 Email`, `📛 FirstName`} $\rightarrow$ `📛 FirstName`. 👉 {📧, 📛} ➡️ 📛

### 2. Augmentation Axiom ➕

If A functionally determines B ($A \rightarrow B$), then adding an attribute C to A still means that the augmented set (A and C) functionally determines B (A, C $\rightarrow$ B). If knowing A is enough to know B, then knowing A *and* something else (C) is still enough to know B.

**Concept:** If knowing some information lets you know another fact, then having that original information *plus* some extra information still lets you know that same fact. The extra information doesn't break the existing dependency.

**Formal Notation:** If $A \rightarrow B$, then $A \cup C \rightarrow B$.

**Example:**

If `StudentID` $\rightarrow$ `🏠 Major` (Knowing a student's ID tells you their major), then adding `📅 EnrollmentDate` to the left side doesn't change the fact that you can still determine the `🏠 Major`.

`StudentID` $\rightarrow$ `🏠 Major` 👉 StudentID ➡️ 🏠

Therefore, {`StudentID`, `📅 EnrollmentDate`} $\rightarrow$ `🏠 Major`. 👉 {StudentID, 📅} ➡️ 🏠

### 3. Transitivity Axiom 🔃

If A functionally determines B ($A \rightarrow B$), and B functionally determines C ($B \rightarrow C$), then A functionally determines C ($A \rightarrow C$). This is like the transitive property in mathematics.

**Concept:** If the first thing tells you the second thing, and the second thing tells you the third thing, then the first thing indirectly tells you the third thing.

**Formal Notation:** If $A \rightarrow B$ and $B \rightarrow C$, then $A \rightarrow C$.

**Example:**

If `StudentID` $\rightarrow$ `🏠 Major` (Knowing the StudentID tells you the Major), and `🏠 Major` $\rightarrow$ `🧑‍🏫 DepartmentHead` (Knowing the Major tells you the Department Head), then `StudentID` $\rightarrow$ `🧑‍🏫 DepartmentHead`.

`StudentID` $\rightarrow$ `🏠 Major` 👉 StudentID ➡️ 🏠
`🏠 Major` $\rightarrow$ `🧑‍🏫 DepartmentHead` 👉 🏠 ➡️ 🧑‍🏫

Therefore, `StudentID` $\rightarrow$ `🧑‍🏫 DepartmentHead`. 👉 StudentID ➡️ 🧑‍🏫

### Derived Rules ✨

While these three axioms are complete, other useful inference rules can be derived from them, such as:

* **Union Rule:** If $A \rightarrow B$ and $A \rightarrow C$, then $A \rightarrow B \cup C$. (If A determines B and A determines C, A determines both B and C).
* **Decomposition Rule:** If $A \rightarrow B \cup C$, then $A \rightarrow B$ and $A \rightarrow C$. (If A determines B and C, it determines B individually and C individually).
* **Pseudotransitivity Rule:** If $A \rightarrow B$ and $CB \rightarrow D$, then $AC \rightarrow D$.

Armstrong's Axioms provide the formal basis for manipulating and reasoning about functional dependencies, which is essential for database design and normalization. They allow us to infer all possible dependencies within a relational schema.

## 📐 Normalization

Normalization is a process of organizing the columns (attributes) and tables (relations) in a relational database to reduce data redundancy and improve data integrity. It involves breaking down a table into smaller tables and defining relationships between them. The goal is to isolate data so that additions, deletions, and modifications of attributes can be made in just one table, thus avoiding inconsistencies.

**Concept:** It's like tidying up your data! You want to store information in a way that avoids repeating yourself and makes sure updates are consistent everywhere. You achieve this by following a set of rules called "normal forms."

**Why Normalize?** 🤔

* **Minimizing Redundancy:** Avoids storing the same information multiple times, saving space and reducing the risk of inconsistencies. 💾❌
* **Improving Data Integrity:** Ensures that data is accurate and consistent across the database. ✅🔒
* **Easier Maintenance:** Makes it simpler to update, delete, or insert data without causing problems in other parts of the database. 🛠️ effortless

**Normal Forms:**

Normalization is typically done in stages, following what are called normal forms. The most common are:

* **First Normal Form (1NF):** Eliminates repeating groups of attributes and ensures that each attribute contains atomic (indivisible) values. 1️⃣
* **Second Normal Form (2NF):** Meets 1NF and ensures that all non-key attributes are fully functionally dependent on the primary key. (Applies to tables with composite primary keys). 2️⃣
* **Third Normal Form (3NF):** Meets 2NF and eliminates transitive dependencies (where a non-key attribute is dependent on another non-key attribute). 3️⃣
* **Boyce-Codd Normal Form (BCNF):** A stricter version of 3NF. (Every determinant is a candidate key). 🔐

**Example of Normalization (Simplistic):**

Let's say we start with a single table `📦 OrderDetails` that is not normalized:

| OrderID | ProductID | ProductName | ProductPrice | CustomerName | CustomerAddress |
|---|---|---|---|---|---|
| 101 | A1 | Laptop | 1000 | Alice | 123 Main St |
| 101 | B2 | Mouse | 25 | Alice | 123 Main St |
| 102 | A1 | Laptop | 1000 | Bob | 456 Oak Ave |

**Problems:**

* **Redundancy:** Customer information (Name, Address) is repeated for each product in an order. Product details (ProductName, ProductPrice) are repeated for each order containing that product. 👎💾
* **Update Anomalies:** If Alice changes her address, you have to update multiple rows. If you delete the last product for an order, you lose the customer information for that order. 🛠️🔄❓

**After Normalization (e.g., towards 3NF):**

We can break this down into three tables:

`🛍️ Orders` table:

| OrderID | CustomerName | CustomerAddress |
|---|---|---|
| 101 | Alice | 123 Main St |
| 102 | Bob | 456 Oak Ave |

`🍎 Products` table:

| ProductID | ProductName | ProductPrice |
|---|---|---|
| A1 | Laptop | 1000 |
| B2 | Mouse | 25 |

`🛒 OrderItems` table (linking Orders and Products):

| OrderID | ProductID |
|---|---|
| 101 | A1 |
| 101 | B2 |
| 102 | A1 |

**Benefits:**

* Customer information is stored only once in `🛍️ Orders`.
* Product information is stored only once in `🍎 Products`.
* Relationships are managed in `🛒 OrderItems`.
* Updates are easier and inconsistencies are avoided. ✅✨

Functional dependencies are the rules that guide the normalization process, helping us identify how to decompose tables correctly to achieve the desired normal form.

Alright, let's talk about the Ullman Algorithm! This algorithm is a practical way to use the concepts of functional dependencies and Armstrong's Axioms to find the closure of a set of attributes.

# ⚙️ The Ullman Algorithm (for Attribute Closure)

The Ullman Algorithm is used to compute the **attribute closure** of a set of attributes X with respect to a set of functional dependencies F. The closure of X, denoted as $X^+$, is the set of all attributes that are functionally dependent on X. In other words, it's all the attributes you can determine if you know the values of the attributes in X.

**Concept:** Given some attributes, this algorithm helps you figure out *all* other attributes you can logically deduce from them based on the rules (functional dependencies) you have.

**The Algorithm Steps:**

1.  **Initialization:** Start with a result set that is just the initial set of attributes X.
    `Result = X` ✨

2.  **Iteration:** Repeatedly loop through all the functional dependencies in F. If you find a functional dependency $A \rightarrow B$ where all attributes in A are already in your `Result` set, but some attributes in B are not, add those new attributes from B to your `Result` set.
    `For each functional dependency A -> B in F:`
    `If A is a subset of Result:`
    `Add all attributes in B to Result`
    `Repeat until no new attributes can be added to Result.` 🔄

3.  **Termination:** The algorithm stops when a full pass through all functional dependencies in F does not add any new attributes to the `Result` set. The final `Result` set is the closure $X^+$. 🎉

**Why is this useful?** Computing attribute closure is essential for:

* **Finding Candidate Keys:** A set of attributes K is a candidate key if its closure $K^+$ includes all attributes in the relation.
* **Checking Functional Dependency Implication:** To check if a functional dependency $A \rightarrow B$ is implied by a set of dependencies F, you can compute the closure of A ($A^+$) with respect to F. If B is a subset of $A^+$, then the dependency is implied.
* **Normalization:** Understanding closures helps in decomposing tables during the normalization process.

## 📝 Example of Using the Ullman Algorithm

Let's consider a relation R with attributes {A, B, C, D, E} and the following set of functional dependencies F:

1.  $A \rightarrow B$
2.  $BC \rightarrow D$
3.  $E \rightarrow C$
4.  $D \rightarrow A$

We want to find the closure of the set of attributes {E, D}, i.e., $\{E, D\}^+$.

**Step 1: Initialization**

Our initial set of attributes X is {E, D}.
`Result = {E, D}` ✨

**Step 2: Iteration**

Let's go through the functional dependencies and see what we can add to `Result`.

* **Dependency 1: $A \rightarrow B$**
    Is A in `Result` ({E, D})? No. Cannot use this dependency yet.

* **Dependency 2: $BC \rightarrow D$**
    Are B and C in `Result` ({E, D})? No (C is missing). Cannot use this dependency yet.

* **Dependency 3: $E \rightarrow C$**
    Is E in `Result` ({E, D})? Yes. Add C to `Result`.
    `Result = {E, D, C}` ✨➕C

* **Dependency 4: $D \rightarrow A$**
    Is D in `Result` ({E, D, C})? Yes. Add A to `Result`.
    `Result = {E, D, C, A}` ✨➕A

Now, we repeat the pass through the dependencies with the updated `Result` set.

* **Dependency 1: $A \rightarrow B$**
    Is A in `Result` ({E, D, C, A})? Yes. Add B to `Result`.
    `Result = {E, D, C, A, B}` ✨➕B

* **Dependency 2: $BC \rightarrow D$**
    Are B and C in `Result` ({E, D, C, A, B})? Yes (B and C are both in `Result`). Is D already in `Result`? Yes. Nothing new to add from this dependency in this pass.

* **Dependency 3: $E \rightarrow C$**
    Is E in `Result`? Yes. Is C already in `Result`? Yes. Nothing new.

* **Dependency 4: $D \rightarrow A$**
    Is D in `Result`? Yes. Is A already in `Result`? Yes. Nothing new.

We have completed a pass through all dependencies and did not add any new attributes to `Result`.

**Step 3: Termination**

The algorithm stops. The closure of {E, D} is the final `Result` set.

$\{E, D\}^+ = \{A, B, C, D, E\}$ 🎉

In this example, knowing the values of attributes E and D allows us to determine the values of all other attributes in the relation based on the given functional dependencies. This means that {E, D} is a candidate key for this relation.

The Ullman Algorithm provides a systematic way to compute attribute closures, which is a fundamental operation in relational database theory and design.

Let's clarify the concepts of "s+" and "s-" based on standard database theory, where "s-" aligns with a Minimal Cover and "s+" aligns with the Closure of a set of Functional Dependencies.

## ✨ The Closure of a Set of Functional Dependencies (Your "s+")

The closure of a set of functional dependencies S, denoted as $S^+$ (or $\Sigma^+$), is the complete set of *all* functional dependencies that can be logically derived from S using Armstrong's Axioms.

**Concept:** If S is your initial set of rules about how attributes relate, $S^+$ represents *every single rule* (functional dependency) that is implicitly true because of your initial rules in S. It's the full set of all possible dependencies implied by your given set. 🌌

**How is $S^+$ determined?**

You use Armstrong's Axioms (Reflexivity, Augmentation, and Transitivity, plus their derived rules like Union and Decomposition) to infer new functional dependencies from the ones in S. You keep applying these rules until no new functional dependencies can be generated. The resulting collection of all dependencies is $S^+$.

**Example:**

Let S = {$A \rightarrow B$, $B \rightarrow C$}

Using the Transitivity Axiom:
Since $A \rightarrow B$ and $B \rightarrow C$, we can infer $A \rightarrow C$. 👉 $A \rightarrow C$ is in $S^+$.

Using the Augmentation Axiom:
Since $A \rightarrow B$, we can infer $AC \rightarrow B$. 👉 $AC \rightarrow B$ is in $S^+$.
Since $B \rightarrow C$, we can infer $AB \rightarrow C$. 👉 $AB \rightarrow C$ is in $S^+$.

Using the Reflexivity Axiom:
For any set of attributes X within the schema, $X \rightarrow X$ is in $S^+$. For example, $A \rightarrow A$, $B \rightarrow B$, $A \rightarrow A$, $AB \rightarrow AB$, etc. These are called trivial dependencies.

The closure $S^+$ for S = {$A \rightarrow B$, $B \rightarrow C$} would include:

* The original dependencies: $A \rightarrow B$, $B \rightarrow C$
* The inferred dependency: $A \rightarrow C$
* Dependencies derived by augmentation (e.g., $AC \rightarrow B$, $AB \rightarrow C$)
* Trivial dependencies (e.g., $A \rightarrow A$, $AB \rightarrow A$)

$S^+$ represents the complete picture of all functional constraints implied by your initial set S.

## 📏 Minimal Cover (Your "s-")

A Minimal Cover, often denoted as $S_{min}$, for a set of functional dependencies S is a simplified set of functional dependencies that is equivalent to S. This means that the closure of the minimal cover is exactly the same as the closure of the original set: $S_{min}^+ = S^+$.

**Concept:** While $S^+$ is the complete set of all implied rules, a Minimal Cover is the smallest, most streamlined set of initial rules that still allows you to generate that complete set $S^+$. It's a non-redundant and simplified representation of the fundamental dependencies. ✂️

**Relationship between $S^+$ and $S_{min}$:**

* Both $S$ (the original set of dependencies) and $S_{min}$ (the minimal cover) have the same closure, $S^+$.
* $S^+$ is a unique set of all implied functional dependencies.
* A Minimal Cover ($S_{min}$) is one of potentially several possible minimal sets of dependencies that generate $S^+$.

Think of it this way:

You start with an initial set of rules (S). 👇
You can use Armstrong's Axioms to discover *all* the rules that are implied by S. This is $S^+$. 🌌
You can also find a smaller, simplified set of initial rules ($S_{min}$) that would generate the *exact same* complete set of implied rules ($S^+$). This is the Minimal Cover. 📏

Your "s-" is likely referring to this Minimal Cover, the most concise representation of the functional dependencies that define the same set of constraints as your original set S.

It's important to remember that while "s+" and "s-" might be used in your specific materials, the standard and widely recognized terms for these concepts are **Closure of a Set of Functional Dependencies ($S^+$)** and **Minimal Cover ($S_{min}$)**.