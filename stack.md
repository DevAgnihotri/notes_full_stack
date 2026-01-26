# ✅ **MONGODB — COMPLETE & DETAILED NOTES**

## **1. MongoDB Fundamentals**

### **• What is MongoDB**

MongoDB is a NoSQL, document-oriented database that stores data in flexible JSON-like documents instead of tables and rows. It is schema-free, meaning every document can have different fields. It is optimized for high performance, scalability, and real-time applications.

### **• NoSQL vs SQL**

SQL databases use tables, rows, and fixed schemas, making them strict but relational. NoSQL like MongoDB uses collections and documents, allowing dynamic structure and easy scaling. SQL fits structured relationships, while NoSQL fits fast-changing and large-scale data environments.

### **• Use cases**

MongoDB is used for real-time apps, e-commerce catalogs, IoT platforms, gaming data, analytics pipelines, and social networks. These use cases require flexible schemas, fast writes, horizontal scaling, and large unstructured data support.

### **• MongoDB architecture**

MongoDB uses a distributed architecture that supports replication for high availability and sharding for horizontal scaling. The architecture includes a primary node for writes and secondary nodes for reads and failover. Data is stored as BSON and accessed over a binary protocol.

### **• BSON**

BSON (Binary JSON) is MongoDB's internal data format designed for speed and type richness. It supports additional data types like `Date`, `ObjectId`, and `Binary` not available in plain JSON. It makes storage efficient and enables fast parsing.

### **• Document-oriented DB**

Document-oriented databases store data as documents grouped into collections instead of rows in tables. Documents resemble JSON objects, making them easy to map to modern application code. This model allows nested objects and arrays directly inside documents.

---

## **2. Core Concepts**

### **• Database**

A MongoDB database is a container for collections. It groups logically related data together (example: `users`, `orders`, `products`). You can create multiple databases within a MongoDB server.

### **• Collection**

A collection is similar to a table in SQL but stores documents instead of rows. Collections have no enforced schema, allowing documents to vary in structure. It is efficient for evolving application data models.

### **• Document**

A document is the basic record stored in MongoDB. It is a JSON-like object containing key-value pairs, arrays, and nested objects. Documents are flexible and map well to programming language objects.

### **• _id & ObjectId**

Every document has an `_id` field as a unique identifier. If not provided, MongoDB generates an `ObjectId`, which encodes timestamp, machine ID, and process information for uniqueness. `_id` helps with indexing and retrieval efficiency.

### **• Schema-less nature**

MongoDB does not enforce a fixed schema at the database level, letting documents evolve over time. This is useful for agile development where new fields can be added without migrations. Schemas can still be enforced at the application layer if needed.

---

## **3. Data Types**

### **• String**

Stores UTF-8 text data like names, emails, titles, etc.

### **• Number**

Supports both integers and floating-point values for mathematical operations.

### **• Boolean**

Stores `true` or `false` values used for conditions and feature flags.

### **• Array**

Stores lists of values such as tags, skills, or nested objects.

### **• Object**

Stores embedded document structures to represent related data inside a parent document.

### **• Date**

Stores date-time objects useful for logs, timestamps, and scheduling.

### **• ObjectId**

Special 12-byte identifier automatically generated for `_id` values.

### **• Null**

Represents empty or missing values in fields to indicate absence.

---

## **4. CRUD Operations**

### **• insertOne**

Inserts a single document into a collection, useful for saving single user records or logs.

### **• insertMany**

Inserts multiple documents at once, improving performance for bulk writes.

### **• find**

Returns multiple matching documents as a cursor, commonly used for listing data.

### **• findOne**

Returns the first matching document, useful for login or profile lookups.

### **• updateOne**

Modifies a single document that matches a specified filter, often with `$set`.

### **• updateMany**

Updates all matching documents, useful for batch operations like setting status fields.

### **• deleteOne**

Deletes the first matching entry, typically used for removing a single resource.

### **• deleteMany**

Removes all documents matching a condition, used for cleanup tasks.

### **• replaceOne**

Replaces an entire document rather than updating fields, used for full overwrite cases.

---

## **5. Querying (Deep)**

### **• Comparison operators (`$eq $gt $lt`)**

Used to compare field values (equal, greater than, less than) for numeric and string filters.

### **• Logical operators (`$and $or $not`)**

Combine conditions to match complex rules such as multiple filters or exclusions.

### **• `$in / $nin`**

Match values that belong or do not belong to a given array, useful for filters like categories or roles.

### **• Projection**

Controls which fields appear in the result, improving performance by excluding unused data.

### **• Sorting**

Sorts results in ascending or descending order, commonly used for listing data chronologically.

### **• Limit & skip**

Used together to restrict results and implement pagination by defining page size and offset.

### **• Pagination patterns**

Common patterns include skip-limit, range queries, and bookmark-based pagination for scalable APIs.

---

## **6. Indexing**

### **• What is index**

An index is a data structure that speeds up read queries similar to an index in a book. Without indexes, MongoDB scans documents sequentially.

### **• Single-field index**

Index on one field (example: `email`) to speed equality lookups and sorting.

### **• Compound index**

Indexes multiple fields in a single structure, useful for combined queries like `city + age`.

### **• Text index**

Allows full-text search on string fields with stemming and scoring.

### **• Unique index**

Forces uniqueness on a field like `email` to prevent duplicate user records.

### **• Index performance**

Indexes improve read performance but slow down writes because indexes must update on inserts.

### **• Explain plan**

Used to inspect how MongoDB executes queries and whether indexes are being used efficiently.

---

## **7. Aggregation Framework (VERY IMPORTANT)**

### **• Aggregation pipeline**

A multi-stage data processing pipeline similar to SQL `GROUP BY + JOIN`. Each stage transforms documents step-by-step.

### **• `$match`**

Filters documents based on conditions, similar to SQL `WHERE`.

### **• `$group`**

Groups documents by a field and performs aggregations like `sum`, `avg`, `count`.

### **• `$project`**

Shapes the output by including, excluding, or computing fields.

### **• `$lookup`**

Performs a left outer join across collections to simulate relational behavior.

### **• `$unwind`**

Deconstructs arrays into multiple documents for detailed processing.

### **• `$sort`**

Reorders data on specified fields for ranking or ordering.

### **• `$limit`**

Restricts the number of output documents, useful in pagination.

### **• `$facet`**

Executes multiple pipelines in parallel to produce multi-view results.

---

## **8. Relationships**

### **• Embedded documents**

Related data stored inside the main document for fast reads, useful for one-to-few cases like addresses in users.

### **• Referenced documents**

Stores relationship via `_id` references, useful when data grows large or reused frequently.

### **• One-to-One**

One document relates to exactly one other, stored embedded or referenced.

### **• One-to-Many**

One parent relates to multiple children, often represented as arrays or separate referenced collection.

### **• Many-to-Many**

Both sides relate to multiple documents, handled using arrays of IDs or join collections.

### **• Design trade-offs**

Embedding is faster for reads but grows document size; referencing reduces size but may require multiple queries.

---

## **9. Transactions**

### **• ACID properties**

MongoDB transactions support Atomicity, Consistency, Isolation, Durability to ensure reliable multi-step operations.

### **• Multi-document transactions**

Allow updates across multiple documents or collections as a single atomic unit, mainly for financial or critical updates.

### **• Sessions**

Transactions run inside sessions, which track state across multiple database operations.

---

## **10. Performance & Optimization**

### **• Query optimization**

Uses indexes, projections, and efficient filters to reduce document scanning.

### **• Index tuning**

Choosing proper indexes improves reads, while avoiding unnecessary indexes prevents write slowdowns.

### **• Read/write performance**

Balanced through replication, write concerns, and sharding strategies depending on workload.

### **• Schema design patterns**

Common patterns include bucket, subset, referencing, and embedding for scalable and efficient data models.

---

## **11. Security (Conceptual)**

### **• Authentication**

Ensures only trusted clients can connect by validating identities (SCRAM, X.509).

### **• Authorization**

Controls what authenticated users can access using role-based permissions.

### **• Roles**

Predefined roles like `readWrite`, `dbAdmin`, or custom roles define user privileges.

### **• Data protection basics**

Includes transport encryption (TLS), audit logs, access control, and secure backup strategies.

---

# ✅ **MONGOOSE — COMPLETE & DETAILED NOTES**

## **1. Mongoose Basics**

### **• What is Mongoose**

Mongoose is an **Object Data Modeling (ODM) library** for MongoDB and Node.js. It provides a **schema-based structure** to work with MongoDB documents. Mongoose helps manage validation, casting, query building, and business logic in a structured way.

### **• ODM vs ORM**

ODM (Object Data Modeling) maps **objects in code to database documents**, while ORM (Object Relational Mapping) maps objects to relational database tables. Mongoose is ODM because MongoDB is document-oriented.

### **• Why Mongoose**

It provides:

* **Schema enforcement** (even on schema-less MongoDB)
* **Validation** (built-in + custom)
* **Middleware hooks**
* **Populate / relationships**
* Cleaner, maintainable code

### **• Connecting to MongoDB**

You can connect using `mongoose.connect()` with URI. Example:

```js
import mongoose from 'mongoose';

mongoose.connect('mongodb://localhost:27017/mydb')
  .then(() => console.log('DB connected'))
  .catch(err => console.error(err));
```

---

## **2. Schema**

### **• Schema definition**

A schema defines the structure of documents in a collection, including fields and types. Example:

```js
const userSchema = new mongoose.Schema({
  name: String,
  email: String,
  age: Number
});
```

### **• Data types**

Supported types: `String`, `Number`, `Boolean`, `Date`, `Buffer`, `ObjectId`, `Array`, `Mixed`.

### **• Required fields**

Mark a field mandatory:

```js
name: { type: String, required: true }
```

### **• Default values**

Set defaults if value is missing:

```js
role: { type: String, default: 'user' }
```

### **• Enum**

Restrict a field to certain values:

```js
status: { type: String, enum: ['active', 'inactive'] }
```

### **• Min / Max**

Set numeric or date constraints:

```js
age: { type: Number, min: 18, max: 60 }
```

### **• Schema options**

Global options like timestamps, versioning:

```js
new mongoose.Schema({ name: String }, { timestamps: true });
```

---

## **3. Models**

### **• Creating models**

A model binds a schema to a collection.

```js
const User = mongoose.model('User', userSchema);
```

### **• Model methods**

Default methods like `.create()`, `.find()`, `.updateOne()` are available.

### **• Static methods**

Custom methods on models:

```js
userSchema.statics.findByEmail = function(email) {
  return this.findOne({ email });
};
```

---

## **4. CRUD Operations**

### **• create**

Insert a single document:

```js
User.create({ name: 'Dev', email: 'dev@example.com' });
```

### **• insertMany**

Insert multiple documents at once:

```js
User.insertMany([{ name: 'A' }, { name: 'B' }]);
```

### **• find**

Retrieve multiple documents:

```js
User.find({ age: { $gte: 18 } });
```

### **• findOne**

Return the first match:

```js
User.findOne({ email: 'dev@example.com' });
```

### **• findById**

Get document by `_id`:

```js
User.findById('64d9ab123...');
```

### **• updateOne**

Update first matching document:

```js
User.updateOne({ name: 'Dev' }, { $set: { age: 25 } });
```

### **• findByIdAndUpdate**

Update by `_id` and optionally return new doc:

```js
User.findByIdAndUpdate(id, { age: 26 }, { new: true });
```

### **• deleteOne**

Delete first matching document:

```js
User.deleteOne({ email: 'a@example.com' });
```

### **• findByIdAndDelete**

Delete by `_id`:

```js
User.findByIdAndDelete(id);
```

---

## **5. Validation**

### **• Built-in validation**

Mongoose supports required, min/max, enum, match (regex), and type checks automatically.

### **• Custom validators**

You can add custom logic:

```js
age: { 
  type: Number, 
  validate: value => value > 0 
}
```

### **• Async validation**

Validators can be async, e.g., check DB for uniqueness.

### **• Error handling**

Validation errors throw `ValidationError`, can be caught in `try/catch`.

---

## **6. Middleware (Hooks)**

### **• pre hooks**

Executed **before** an action:

```js
userSchema.pre('save', function(next) {
  console.log('Before save');
  next();
});
```

### **• post hooks**

Executed **after** action:

```js
userSchema.post('save', doc => console.log('Saved:', doc));
```

### **• save / remove / update / findOneAndUpdate**

Hooks can be applied on these operations to run logic automatically before or after.

---

## **7. Virtuals**

### **• Virtual fields**

Fields not stored in DB but computed:

```js
userSchema.virtual('fullName').get(function() {
  return `${this.firstName} ${this.lastName}`;
});
```

### **• Computed properties**

Calculate values dynamically based on other fields.

### **• Populate virtuals**

Virtual fields can also be used to reference related documents without storing foreign keys.

---

## **8. Population**

### **• populate()**

Populate references to get related documents:

```js
User.find().populate('friends');
```

### **• References**

Link documents by `_id` to simulate relationships (one-to-many, etc.).

### **• Deep population**

Nested populate, e.g., posts → comments → users.

### **• Performance concerns**

Populate adds extra queries, can slow down large collections; consider aggregation pipeline.

---

## **9. Query Helpers**

### **• Custom query helpers**

Add reusable query methods:

```js
userSchema.query.byName = function(name) {
  return this.where({ name: name });
};
```

### **• Chaining queries**

Query helpers can be chained:

```js
User.find().byName('Dev').limit(5);
```

---

## **10. Indexing**

### **• Schema-level indexes**

Define indexes in schema for faster queries:

```js
userSchema.index({ email: 1 });
```

### **• Unique indexes**

Enforce unique values:

```js
userSchema.index({ email: 1 }, { unique: true });
```

### **• Performance tuning**

Indexes improve read speed but slow writes; balance is needed for performance.

---

## **11. Transactions**

### **• Sessions**

Transactions run in session objects:

```js
const session = await mongoose.startSession();
```

### **• Atomic operations**

Multiple operations within a transaction either **all succeed or all fail**, ensuring ACID compliance.

---

## **12. Error Handling**

### **• ValidationError**

Occurs when validation fails on schema rules.

### **• CastError**

Occurs when an invalid type is assigned (e.g., string instead of number).

### **• Duplicate key error**

Occurs when unique index is violated.

### **• Custom error handling**

You can catch and customize messages in try/catch blocks for better UX.

---

# ✅ **PRISMA — COMPLETE & DETAILED NOTES**

## **1. Prisma Fundamentals**

### **• What is Prisma**

Prisma is a modern **ORM (Object Relational Mapping) tool** that allows developers to interact with databases using type-safe queries. It supports multiple databases (PostgreSQL, MySQL, SQLite, MongoDB) and generates a client to query data with auto-completion and type checking. Prisma makes database operations easier and less error-prone in Node.js.

### **• Prisma vs Mongoose**

Mongoose is an **ODM** specifically for MongoDB and works with schema-less documents. Prisma is an **ORM**, designed primarily for relational databases but also supports MongoDB. Prisma provides type-safe queries and automated migrations, while Mongoose focuses on flexible document structure and hooks.

### **• ORM concepts**

ORM maps objects in application code to database tables. It allows working with databases in an object-oriented way instead of raw SQL. ORMs handle query generation, relationships, and data consistency.

### **• When to use Prisma**

Use Prisma when building applications that need **type safety**, **structured queries**, **migrations**, and multi-database support. It is especially useful for **Node.js + TypeScript projects** with relational databases or MongoDB with structured documents.

---

## **2. Prisma Setup**

### **• Prisma CLI**

The Prisma CLI is used to initialize projects, generate client code, and run migrations. Example commands:

```bash
npm install prisma --save-dev
npx prisma --help
```

### **• prisma init**

Initializes a Prisma project. It creates:

* `prisma/schema.prisma` file
* `.env` file for database credentials

```bash
npx prisma init
```

### **• Environment variables**

Database connection URLs are stored in `.env` for security. Example:

```
DATABASE_URL="postgresql://user:pass@localhost:5432/mydb"
```

### **• Datasource config**

Defines which database Prisma will connect to. Example in `schema.prisma`:

```prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}
```

---

## **3. Prisma Schema**

### **• schema.prisma**

Central file where all models, fields, and relations are defined. It acts as the blueprint for the database structure.

### **• Models**

Models define tables/collections in the database. Example:

```prisma
model User {
  id    String @id @default(uuid())
  name  String
  posts Post[]
}
```

### **• Fields**

Each model has fields representing columns. Fields can have types, default values, and constraints.

### **• Data types**

Supports types like `String`, `Int`, `Float`, `Boolean`, `DateTime`, `Json`, and `BigInt`.

### **• Enums**

Restrict fields to predefined values:

```prisma
enum Role {
  USER
  ADMIN
}
```

### **• Relations**

Define relationships between models:

```prisma
model Post {
  id     String @id @default(uuid())
  title  String
  author User   @relation(fields: [authorId], references: [id])
  authorId String
}
```

---

## **4. Migrations**

### **• prisma migrate dev**

Creates and applies migrations during development. Updates database structure as defined in the schema.

### **• migrate deploy**

Applies migrations to production environments.

### **• Reset migrations**

Resets database and reapplies all migrations:

```bash
npx prisma migrate reset
```

### **• Migration history**

Prisma keeps a `_prisma_migrations` table to track applied migrations, ensuring consistency across environments.

---

## **5. Prisma Client**

### **• Prisma Client generation**

Generates a type-safe client to query the database:

```bash
npx prisma generate
```

### **• CRUD operations**

* **create**: insert a new record

```ts
prisma.user.create({ data: { name: 'Dev' } })
```

* **findUnique**: fetch a single record by unique field

```ts
prisma.user.findUnique({ where: { id: '1' } })
```

* **findMany**: fetch multiple records

```ts
prisma.user.findMany({ where: { role: 'USER' } })
```

* **update**: modify existing record

```ts
prisma.user.update({ where: { id: '1' }, data: { name: 'Updated' } })
```

* **delete**: remove a record

```ts
prisma.user.delete({ where: { id: '1' } })
```

* **upsert**: update if exists, else create

---

## **6. Relations (Deep)**

### **• One-to-One**

Each record in one model corresponds to one record in another:

```prisma
model Profile {
  id     String @id @default(uuid())
  user   User   @relation(fields: [userId], references: [id])
  userId String
}
```

### **• One-to-Many**

One record maps to multiple related records:

```prisma
model User {
  posts Post[]
}
```

### **• Many-to-Many**

Both sides can have multiple relations, Prisma uses a junction table internally:

```prisma
model Student {
  courses Course[] @relation("Enrollment")
}
model Course {
  students Student[] @relation("Enrollment")
}
```

### **• Nested writes**

Create/update related records in one query:

```ts
prisma.user.create({
  data: { 
    name: 'Dev',
    posts: { create: { title: 'First Post' } }
  }
})
```

### **• Referential actions**

Define behavior on delete/update, e.g., `CASCADE`, `SET NULL`:

```prisma
author User @relation(fields: [authorId], references: [id], onDelete: Cascade)
```

---

## **7. Querying**

### **• Filtering**

Use `where` to filter results:

```ts
prisma.user.findMany({ where: { age: { gte: 18 } } })
```

### **• Sorting**

Use `orderBy` to sort results:

```ts
prisma.user.findMany({ orderBy: { name: 'asc' } })
```

### **• Pagination**

Use `skip` and `take`:

```ts
prisma.user.findMany({ skip: 10, take: 5 })
```

### **• select**

Pick only specific fields:

```ts
prisma.user.findMany({ select: { name: true, email: true } })
```

### **• include**

Include related models:

```ts
prisma.user.findMany({ include: { posts: true } })
```

---

## **8. Transactions**

### **• Interactive transactions**

Use `$transaction` to ensure multiple queries succeed together:

```ts
await prisma.$transaction([
  prisma.user.create({ data: { name: 'A' } }),
  prisma.post.create({ data: { title: 'Hello' } })
]);
```

### **• Batch transactions**

Perform multiple queries in one atomic operation, ensuring ACID compliance.

---

## **9. Middleware**

### **• Prisma middleware**

Functions run before/after any query, useful for logging, validation, or modification.

### **• Query interception**

You can inspect or modify query parameters dynamically.

### **• Logging queries**

Middleware can log every query for debugging:

```ts
prisma.$use(async (params, next) => {
  console.log(params.model, params.action)
  return next(params)
})
```

---

## **10. Performance**

### **• Query optimization**

Filter unnecessary fields with `select` and use `where` conditions to reduce load.

### **• Indexes**

Add indexes at database level for fast lookups on frequently queried fields.

### **• Connection pooling**

Prisma client reuses connections, reducing overhead on multiple queries.

---

## **11. Prisma + MongoDB**

### **• MongoDB connector**

Prisma supports MongoDB, mapping collections to models. Use `provider = "mongodb"` in schema.

### **• ObjectId handling**

MongoDB `_id` maps to `String` or `ObjectId` in Prisma. Must handle conversion in queries.

### **• Limitations**

MongoDB support is partial: no full relational constraints, limited nested writes, fewer aggregate features.

### **• Best practices**

Use lightweight schema design, limit deep relations, and combine Prisma with aggregation pipelines for advanced operations.

---

## **12. Production Best Practices**

### **• Schema changes**

Use migrations carefully to avoid data loss. Always generate a new migration after schema changes.

### **• Data safety**

Backup database before applying migrations. Enable validation and referential integrity.

### **• Migration strategy**

Use separate environments: dev → staging → production. Test migrations in staging first.

### **• Version control**

Commit `schema.prisma`, migration files, and `.env.example` for team consistency and CI/CD pipelines.

---