# NanoDB

A fast, lightweight, JSON-based NoSQL database library for Android with MongoDB-like collection support and annotation processor-driven schema definitions. NanoDB makes it easy to manage complex data with primary keys, nullable fields, indexing, and smooth migrations — all optimized for performance.

---

## Features

- JSON document storage with collections like MongoDB
- Annotation processor support for defining schema:
  - `@PrimaryKey` to mark unique identifiers
  - `@Nullable` for optional fields
  - `@Indexed` for indexed fields to speed up queries
  - Additional annotations like `@Ignore`, `@CollectionName`
- Easy CRUD operations with fluent API
- Powerful query support (filtering, sorting, pagination)
- Schema versioning and easy migration framework
- Optimized performance via generated adapters and caching
- Supports nested objects and lists
- Optional encryption and backup support

---

## Getting Started

### Installation

Add the NanoDB dependency to your project:

```
implementation 'com.magnatesage.nanodb:nanodb:1.0.0'
```

### Usage

Define your data models using NanoDB annotations:

```
@CollectionName("users")
data class User(
  @PrimaryKey val id: String,
  val name: String,
  @Nullable val email: String?,
  @Indexed val age: Int
)
```

Initialize the database and perform operations:

```
val db = NanoDB.getInstance(context)

db.insert(User("1", "John Doe", "john@example.com", 30))
val users = db.query<User> { it.age > 18 }
```

---

## Migration

Manage schema changes easily with versioning:

```
NanoDB.migrate(1) { oldData ->
  // transform oldData to new schema format
}
```

---

## Documentation

Detailed documentation and examples are available in the [Wiki](#) and [Examples](#) folder.

---

## Contributing

Contributions are welcome! Please open issues or pull requests on GitHub.

---

## License

NanoDB is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Contact

For questions or support, open an issue or reach out via email: support@magnatesage.com
