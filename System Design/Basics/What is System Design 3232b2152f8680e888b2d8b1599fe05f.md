# What is System Design?

**System Design** is the process of **defining the architecture, components, modules, interfaces, and data flow of a system to meet specific requirements such as scalability, reliability, and performance.**

In simple terms:

**System Design = Planning how a software system will be built and how all its parts will work together.**

It answers questions like:

- What **components/services** will the system have?
- How will these components **communicate**?
- How will data be **stored and retrieved**?
- How will the system **scale to millions of users**?
- How will it remain **reliable and fault-tolerant**?

Example:

Designing **YouTube** would involve deciding:

- Frontend clients (web/mobile)
- API servers
- Video storage
- CDN for streaming
- Databases
- Load balancers
- Caching layers

So the **goal of system design** is to build a system that is:

- **Scalable**
- **Reliable**
- **Efficient**
- **Maintainable**

## Distributed Systems

A **Distributed System** is a system where **multiple computers (nodes) work together over a network to appear as a single system to the user.**

In simple terms:

**Distributed System = Many machines working together to solve one problem.**

Key idea:

- The work is **distributed across multiple machines** instead of running on just one computer.

Example:

- **Google Search**
- **Netflix**
- **Amazon**

These systems run on **thousands of servers** across the world, but users experience them as **one single service**.

Main characteristics:

- **Multiple machines**
- **Network communication**
- **Shared workload**
- **Fault tolerance** (if one machine fails, others continue)
- **Scalability** (can add more machines when needed)

Short definition for interviews:

**A distributed system is a collection of independent computers that communicate over a network and coordinate their actions to function as a single system.**

## Horizontal vs Vertical scaling

### Vertical Scaling (Scale Up)

**Vertical scaling** means **increasing the power of a single machine** by adding more resources.

Examples of resources:

- More **CPU**
- More **RAM**
- More **storage**

Example:

Upgrading a server from **8 GB RAM → 64 GB RAM**.

**Definition:**

Vertical scaling is the process of **increasing the capacity of a single server by adding more hardware resources.**

---

### Horizontal Scaling (Scale Out)

**Horizontal scaling** means **adding more machines (servers)** to handle the load.

Instead of making one server stronger, you **add multiple servers**.

Example:

1 server → 10 servers behind a load balancer.

**Definition:**

Horizontal scaling is the process of **increasing system capacity by adding more machines to distribute the workload.**

---

### Quick Difference

| Vertical Scaling | Horizontal Scaling |
| --- | --- |
| Scale **up** | Scale **out** |
| Add resources to **one machine** | Add **more machines** |
| Limited by hardware | Can scale almost infinitely |
| Easier to implement | Requires distributed system design |

## Capacity Planning

### Capacity Estimation (Capacity Planning)

**Capacity Estimation** is the process of **predicting how much traffic, storage, and computing power a system needs to handle expected users and data.**

It helps answer questions like:

- How many **servers** do we need?
- How much **storage** is required?
- How much **network bandwidth** is needed?

Engineers estimate these numbers **before designing the system**.

---

## Example: Designing **YouTube**

### 1️⃣ Assume Number of Users

Suppose:

- **1 billion users**
- **10% active daily**

So:

Daily Active Users (DAU)

= **100 million users**

---

### 2️⃣ Requests Per Second

Assume each user watches **5 videos per day**

Total video views per day:

```
100M × 5 = 500M video views/day
```

Convert to **requests per second**

```
500M / 86,400 seconds ≈ 5,800 requests/sec
```

So system must support **~6000 requests/sec** (minimum).

In real systems we plan **3–5× peak load**.

Estimated peak:

```
~20,000 requests/sec
```

---

### 3️⃣ Storage Estimation

Assume:

- **500,000 videos uploaded per day**
- Average video size = **100 MB**

Daily storage:

```
500,000 × 100 MB
= 50,000,000 MB
= 50 TB per day
```

Yearly storage:

```
50 TB × 365 ≈ 18 PB/year
```

(PB = Petabytes)

---

### 4️⃣ Bandwidth Estimation

Assume average video watched = **50 MB**

Daily traffic:

```
500M views × 50 MB
= 25,000,000 MB
= 25 PB/day
```

Bandwidth required:

```
25 PB / 86,400 seconds
≈ 290 GB/sec
```

This is why systems like YouTube rely heavily on **CDNs**.

---

### 5️⃣ Why Capacity Planning Matters

Without estimation:

- Servers crash
- Storage runs out
- Network bottlenecks occur

Capacity planning ensures the system is:

- **Scalable**
- **Reliable**
- **Cost efficient**

---

### Interview One-Line Definition

**Capacity estimation is the process of calculating expected traffic, storage, and system resources required to design a scalable system.**

## Http and Https

**HTTP** is a protocol used to **transfer data between a client (browser) and a server over the internet.**

Characteristics:

- Data is sent in **plain text**
- **Not secure**
- Can be **intercepted or read by attackers**

Example URL:

```
http://example.com
```

Default port:

```
80
```

---

### HTTPS (HyperText Transfer Protocol Secure)

**HTTPS** is the **secure version of HTTP**. It encrypts communication between the client and server using **SSL/TLS encryption**.

Characteristics:

- Data is **encrypted**
- **Secure communication**
- Protects against **man-in-the-middle attacks**
- Used for **logins, payments, banking**

Example URL:

```
https://example.com
```

Default port:

```
443
```

---

### Key Differences

| HTTP | HTTPS |
| --- | --- |
| Not secure | Secure |
| No encryption | Uses SSL/TLS encryption |
| Port 80 | Port 443 |
| Data visible in transit | Data encrypted |

---

### Simple Example

When you log into **Amazon** or **Google**, the website uses **HTTPS** so that your **password and personal data are encrypted** during transmission. 🔐

## Relational Model in DBMS

### Relational Model (DBMS)

The **Relational Model** is a database model where **data is organized into tables (relations) made up of rows and columns.**

Each table represents a **real-world entity**, and relationships between tables are defined using **keys**.

**Definition:**

**The relational model is a way of structuring data in a database using tables (relations), where data is stored in rows (tuples) and columns (attributes).**

---

### Basic Components

**1. Table (Relation)**

A table that stores data about an entity.

Example: `Students`

| StudentID | Name | Age |
| --- | --- | --- |
| 1 | Ali | 21 |
| 2 | Sara | 22 |

---

**2. Row (Tuple)**

A **single record** in a table.

Example:

```
1 | Ali | 21
```

---

**3. Column (Attribute)**

A **property** of the entity.

Example:

```
StudentID, Name, Age
```

---

**4. Primary Key**

A column that **uniquely identifies each row** in a table.

Example:

```
StudentID
```

---

**5. Foreign Key**

A column that **creates a relationship between two tables**.

Example:

`Orders` table referencing `CustomerID` from `Customers`.

---

### Example of Relationship

**Customers Table**

| CustomerID | Name |
| --- | --- |
| 1 | John |
| 2 | Sara |

**Orders Table**

| OrderID | CustomerID |
| --- | --- |
| 101 | 1 |
| 102 | 2 |

Here **CustomerID** in Orders is a **Foreign Key** linking to Customers.

---

### Key Idea

Relational model organizes data in **structured tables with defined relationships**, allowing efficient querying using **SQL**.

---

### One-Line Interview Definition

**The relational model is a database model that organizes data into tables consisting of rows and columns and establishes relationships between them using keys.**

## Database Indexing (SQL and NoSQL)

**Indexing** is a technique used to **speed up data retrieval** from a database by creating a **data structure that allows faster searching of records**.

Without an index, the database must **scan the entire table (full table scan)** to find data.

**Definition:**

**Indexing is a data structure used by databases to quickly locate and access rows without scanning the entire table.**

---

# 1️⃣ Indexing in SQL Databases

Examples of SQL databases:

- MySQL
- PostgreSQL
- Microsoft SQL Server

SQL databases usually use **B-Tree indexes**.

### Example Table

Users table:

| id | name | email |
| --- | --- | --- |
| 1 | Ali | [a@gmail.com](mailto:a@gmail.com) |
| 2 | Sara | [s@gmail.com](mailto:s@gmail.com) |

If we run:

```sql
SELECT * FROM Users WHERE email = 'a@gmail.com';
```

Without index → **Full table scan**

With index → **Direct lookup**

### Create Index Example

```sql
CREATE INDEX idx_email
ON Users(email);
```

### Common SQL Index Types

1. **Primary Index**
    - Created automatically for **Primary Key**
2. **Unique Index**
    - Ensures values are unique
3. **Composite Index**
    - Index on **multiple columns**

Example:

```sql
CREATE INDEX idx_name_age
ON Users(name, age);
```

---

# 2️⃣ Indexing in NoSQL Databases

Examples of NoSQL databases:

- MongoDB
- Apache Cassandra
- Redis

NoSQL indexing depends on **data model type**.

### Example in MongoDB

Collection:

```json
{
 "name": "Ali",
 "age": 25,
 "city": "New York"
}
```

Create index:

```jsx
db.users.createIndex({ age: 1 })
```

Now queries on **age** become faster.

---

# 3️⃣ Why Indexing is Important

Benefits:

- Faster **query performance**
- Efficient **searching**
- Reduced **query time**

Example:

Without index

10 million rows → **scan all rows**

With index

Database jumps **directly to the record**

---

# 4️⃣ Trade-offs of Indexing

Indexes improve **read speed**, but they:

- Increase **storage usage**
- Slow down **insert/update/delete operations**
- Require **maintenance**

---

# Interview One-Line Definition

**Database indexing is a technique used to improve query performance by creating a data structure that allows fast lookup of records without scanning the entire table.**

---

If you want, I can also explain **the 6 most important index types used in System Design interviews (B-Tree, Hash, LSM Tree, Inverted Index, etc.)**. These come up a lot in **Google / Amazon interviews. (Will deep dive later)**

## SQL vs NoSQL Databases

### 1️⃣ SQL Databases (Relational Databases)

**SQL databases** store data in **structured tables with rows and columns**, and relationships between tables are defined using **keys**.

They use **Structured Query Language (SQL)** to query and manage data.

**Examples**

- MySQL
- PostgreSQL
- Microsoft SQL Server

---

### Structure Example

**Users Table**

| id | name | email |
| --- | --- | --- |
| 1 | Ali | [ali@gmail.com](mailto:ali@gmail.com) |
| 2 | Sara | [sara@gmail.com](mailto:sara@gmail.com) |

Query example:

```sql
SELECT * FROM Users WHERE id = 1;
```

---

### Key Characteristics of SQL

- **Structured schema** (fixed table structure)
- **Relationships between tables** using foreign keys
- **ACID transactions** (strong consistency)
- Best for **structured data**

---

### When SQL is Used

- Banking systems
- Financial systems
- Inventory management
- Enterprise applications

Because these systems require **strong consistency and structured data**.

---

# 2️⃣ NoSQL Databases (Non-Relational Databases)

**NoSQL databases** store data in **flexible formats instead of fixed tables**.

They are designed for **large-scale distributed systems and massive data**.

**Examples**

- MongoDB
- Apache Cassandra
- Redis

---

### Example (Document Database)

Document in MongoDB:

```json
{
 "id": 1,
 "name": "Ali",
 "email": "ali@gmail.com"
}
```

Instead of tables, data is stored as **documents**.

---

### Key Characteristics of NoSQL

- **Flexible schema**
- **Highly scalable**
- **Designed for distributed systems**
- Handles **huge amounts of data**

---

### Types of NoSQL Databases

1️⃣ **Key-Value Stores**

Example: Redis

```
user:1 → Ali
```

2️⃣ **Document Databases**

Example: MongoDB

JSON-like documents.

3️⃣ **Column-Family Databases**

Example: Cassandra

Optimized for large-scale analytics.

4️⃣ **Graph Databases**

Example: Neo4j

Used for relationships like social networks.

---

# Key Differences

| SQL | NoSQL |
| --- | --- |
| Structured tables | Flexible data models |
| Fixed schema | Dynamic schema |
| Strong consistency | Often eventual consistency |
| Vertical scaling | Horizontal scaling |
| Best for structured data | Best for large distributed data |

---

# Simple Example

A **banking system** → SQL (strong consistency needed)

A **social media platform storing billions of posts** → NoSQL

---

# One-Line Interview Definition

**SQL databases are relational databases that store structured data in tables, while NoSQL databases store data in flexible formats designed for scalability and distributed systems.**

## Load Balancing

**Load Balancing** is the process of **distributing incoming network traffic across multiple servers so that no single server becomes overloaded.**

**Definition:**

**Load balancing is a technique used to distribute client requests across multiple servers to improve performance, reliability, and scalability.**

---

### Why Load Balancing is Needed

If a system has **only one server**:

- Too many users → server becomes **slow or crashes**

With **multiple servers + load balancer**:

- Traffic is **evenly distributed**
- System becomes **faster and more reliable**

---

### Simple Example

Users → Load Balancer → Servers

```
Users
   |
Load Balancer
  /   |   \
S1   S2   S3
```

- Request 1 → Server 1
- Request 2 → Server 2
- Request 3 → Server 3

This prevents any single server from being overloaded.

---

### Common Load Balancing Algorithms

1. **Round Robin**
    - Requests go sequentially to servers
    - S1 → S2 → S3 → S1
2. **Least Connections**
    - Request goes to server with **fewest active connections**
3. **IP Hash**
    - Same client IP goes to the **same server**

---

### Benefits

- **High availability**
- **Better performance**
- **Scalability**
- **Fault tolerance**

If one server fails, traffic is routed to others.

---

### Real-World Example

Large platforms like **Netflix**, **Amazon**, and **Google** use load balancers to distribute millions of requests across thousands of servers.

---

### One-Line Interview Definition

**Load balancing is the technique of distributing incoming requests across multiple servers to ensure optimal resource utilization, high availability, and system reliability.**

## Sharding

**Sharding** is a technique used in databases to **split large data into smaller pieces and store them across multiple servers (shards).**

Each shard contains **only a portion of the total data**, allowing the system to scale horizontally.

---

### Definition

**Sharding is the process of partitioning a large database into smaller, independent databases (shards) distributed across multiple machines.**

---

### Why Sharding is Needed

When a database grows very large:

- One server cannot handle all the **data size**
- One server cannot handle all the **queries**

Sharding helps by **distributing the data across many servers**.

---

### Example

Suppose we have **100 million users**.

Instead of storing all users in one database:

```
Shard 1 → Users A–H
Shard 2 → Users I–P
Shard 3 → Users Q–Z
```

Now each database server stores **only part of the data**.

---

### How Data is Split

Common sharding strategies:

1️⃣ **Range-based sharding**

```
Shard 1 → UserID 1–1M
Shard 2 → UserID 1M–2M
Shard 3 → UserID 2M–3M
```

2️⃣ **Hash-based sharding**

```
hash(userID) % number_of_shards
```

3️⃣ **Geographic sharding**

```
Shard US → US users
Shard EU → European users
Shard Asia → Asian users
```

---

### Benefits

- **Horizontal scalability**
- **Better performance**
- **Handles massive datasets**
- **Reduced load per database**

---

### Challenges

- Complex queries across shards
- Data rebalancing when adding shards
- Increased system complexity

---

### Real-world Use

Large platforms like **Instagram**, **Twitter**, and **Facebook** use sharding to manage **billions of users and posts**.

---

### One-Line Interview Definition

**Sharding is a database scaling technique that partitions large datasets into smaller pieces stored across multiple servers to improve performance and scalability.**

## Monolith vs Microservices Architecture

## 1) Monolith Architecture

A **monolith** is an architecture where the **entire application is built as one single system**.

That means:

- UI
- business logic
- database access
- authentication
- payments
- notifications

all are part of **one codebase and one deployable unit**.

### Definition

**Monolithic architecture is a software design where all application components are tightly combined into a single codebase and deployed as one unit.**

### Example

Think of an **e-commerce app**.

In monolith:

- User service
- Product catalog
- Cart
- Order management
- Payment

all live inside **one application**.

If you change payment logic, you usually redeploy the **whole app**.

### Real-world style example

A small startup building:

- login
- dashboard
- profile
- billing

might first create everything in **one Spring Boot app** or **one Django app**.

---

## 2) Microservices Architecture

A **microservices architecture** is where the application is split into **small independent services**, and each service handles one specific business capability.

Each service can have:

- its own codebase
- its own database
- its own deployment
- its own team

### Definition

**Microservices architecture is a design approach where an application is divided into small, independent services that communicate over a network.**

### Example

Same **e-commerce app** split into services:

- **User Service**
- **Product Service**
- **Cart Service**
- **Order Service**
- **Payment Service**
- **Notification Service**

Now if payment logic changes, only the **Payment Service** can be updated and deployed.

---

## Simple Mental Model

### Monolith

**One big house**

Everything is inside one building.

### Microservices

**A society of small houses**

Each house has its own purpose, but all work together.

---

## Key Differences

| Monolith | Microservices |
| --- | --- |
| Single codebase | Multiple small services |
| Single deployment | Independent deployments |
| Usually one database | Often separate databases |
| Easier to start | Harder to design initially |
| Harder to scale specific parts | Easier to scale specific services |
| Tightly coupled | Loosely coupled |

---

## Example 1: Netflix style

### Monolith

If Netflix were monolithic:

- streaming
- login
- recommendations
- billing
- search

all would be one giant app.

A failure in one area could affect the whole system.

### Microservices

In microservices:

- Recommendation Service
- Billing Service
- Search Service
- User Service
- Streaming Metadata Service

all work independently.

This is better for very large systems.

---

## Example 2: Banking app

### Monolith

A bank may start with one app containing:

- account management
- transactions
- loans
- customer details

### Microservices

Later it may split into:

- Account Service
- Transaction Service
- Loan Service
- Fraud Detection Service
- Notification Service

This helps separate teams work independently.

---

## Advantages of Monolith

- Simple to build in the beginning
- Easier local development
- Easier testing initially
- Easier deployment at small scale

### Best for

- small projects
- MVPs
- small teams
- early-stage products

---

## Disadvantages of Monolith

- Becomes large and hard to maintain
- Hard to scale only one module
- Small change may require full redeployment
- One bug can impact entire system

---

## Advantages of Microservices

- Independent development
- Independent deployment
- Better scalability
- Better fault isolation
- Teams can own services separately

---

## Disadvantages of Microservices

- More complex architecture
- Network communication overhead
- Harder debugging
- Distributed system problems
- More DevOps and monitoring needed

---

## Interview one-line difference

**Monolith is a single unified application, while microservices split the application into independent services that communicate over a network.**

## When to use which

- Use **Monolith** when the system is small and you want speed of development.
- Use **Microservices** when the system is large, complex, and needs independent scaling and deployment.

## Very short example answer

**Amazon in early stage could be built as a monolith, but at large scale systems like Netflix or Amazon use microservices so different business functions such as payments, orders, and recommendations can scale independently.**