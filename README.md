# Protobuf-Postgres-Extension

A Protobuf extension for annotating `.proto` files with PostgreSQL-specific metadata, enabling seamless schema generation and improving consistency between application and database layers.

## **Features**
- Annotate Protobuf messages with PostgreSQL-specific metadata for:
  - **Table-level properties**: Table names, schemas, indexes, constraints, grants, partitioning.
  - **Column-level properties**: Data types, primary keys, foreign keys, unique constraints.
  - **Advanced PostgreSQL features**: Generated columns, exclusion constraints, deferrable constraints.
- Automate PostgreSQL schema generation using Protobuf tools.
- Maintain alignment between application data models and database schemas.

## **Installation**
1. Clone the repository or download the `postgres_options.proto` file.
2. Include the file in your Protobuf project:
   ```bash
   protoc --proto_path=/path/to/proto --include_imports postgres_options.proto
   ```
3. For Buf CLI users, include the module in your `buf.yaml`:
   ```yaml
   version: v1
   module:
     name: buf.build/your-username/protobuf-postgres-extension
   ```

## **Usage**

### **Basic Example**

```proto
syntax = "proto3";

import "postgres_options.proto";

message User {
  option (postgres.table_name) = "users";
  option (postgres.schema) = "public";

  int32 id = 1 [
    (postgres.column_type) = "SERIAL",
    (postgres.constraints) = [CONSTRAINT_PRIMARY_KEY]
  ];

  string email = 2 [
    (postgres.column_type) = "VARCHAR(255)",
    (postgres.constraints) = [CONSTRAINT_UNIQUE]
  ];
}
```

### **Full Example**
Check the `examples/` directory for a complete example using all supported annotations.

## **Supported PostgreSQL Annotations**

This extension supports the following PostgreSQL-specific annotations, grouped by their level of application.

### **Table-Level Properties**
| Option               | Description                                                                                 |
|----------------------|---------------------------------------------------------------------------------------------|
| `table_name`         | Specifies the table name in PostgreSQL.                                                    |
| `schema`             | Specifies the schema for the table (e.g., `public`).                                        |
| `properties`         | A map of general table properties (e.g., `autovacuum_enabled`).                             |
| `indexes`            | Defines custom indexes for the table.                                                      |
| `partitioning`       | Specifies partitioning details for the table.                                               |
| `grants`             | Lists roles and privileges for the table.                                                   |
| `exclusions`         | Defines exclusion constraints for the table.                                                |

### **Column-Level Properties**
| Option               | Description                                                                                 |
|----------------------|---------------------------------------------------------------------------------------------|
| `column_type`        | Specifies the PostgreSQL data type (e.g., `VARCHAR`, `INT`).                                |
| `constraints`        | Common column constraints, such as `PRIMARY KEY`, `NOT NULL`, `UNIQUE`, or `FOREIGN KEY`.   |
| `default_value`      | Specifies a default value for the column.                                                   |
| `foreign_key`        | Specifies the foreign key reference (e.g., `table.column`).                                 |
| `on_delete`          | Defines the action for `ON DELETE` (e.g., `CASCADE`, `SET NULL`).                           |
| `on_update`          | Defines the action for `ON UPDATE` (e.g., `CASCADE`, `SET NULL`).                           |

### **Index Options**
| Option               | Description                                                                                 |
|----------------------|---------------------------------------------------------------------------------------------|
| `name`               | The name of the index.                                                                      |
| `columns`            | The columns included in the index.                                                         |
| `expression`         | The expression for expression-based indexes.                                                |
| `type`               | The type of the index (e.g., `BTREE`, `GIN`).                                               |
| `unique`             | Specifies whether the index enforces uniqueness.                                            |
| `where_clause`       | A condition for creating a partial index.                                                   |

### **Advanced Properties**
| Option               | Description                                                                                 |
|----------------------|---------------------------------------------------------------------------------------------|
| `generated_column`   | Marks the column as a generated column.                                                     |
| `identity_column`    | Marks the column as an identity column.                                                     |
| `deferrable`         | Marks the column constraint as deferrable.                                                  |
| `initially_deferred` | Marks the column constraint as initially deferred.                                           |

### **Partitioning Options**
| Option               | Description                                                                                 |
|----------------------|---------------------------------------------------------------------------------------------|
| `type`               | Specifies the partitioning type (e.g., `RANGE`, `HASH`, `LIST`).                            |
| `keys`               | Specifies the columns used for partitioning.                                                |

### **Foreign Key Actions**
| Option               | Description                                                                                 |
|----------------------|---------------------------------------------------------------------------------------------|
| `on_delete`          | Specifies the action on delete (e.g., `CASCADE`, `SET NULL`).                               |
| `on_update`          | Specifies the action on update (e.g., `CASCADE`, `SET NULL`).                               |

## **Generated PostgreSQL Schema**

The above `.proto` file generates the following PostgreSQL DDL:

```sql
CREATE TABLE public.users (
  id SERIAL PRIMARY KEY,
  email VARCHAR(255) UNIQUE
);
```

## **Development**

### **Project Structure**
```
protobuf-postgres-extension/
├── postgres/
│   └── v1/
│       └── postgres_options.proto  # Protobuf extension definitions
├── README.md                       # Documentation
├── LICENSE                         # License details
├── examples/                       # Example .proto files
├── tests/                          # Validation test cases
└── buf.yaml                        # Buf Schema Registry configuration
```

### **Buf Commands**
1. **Lint the Protobuf files**:
   ```bash
   buf lint
   ```
2. **Build and validate the module**:
   ```bash
   buf build
   ```
3. **Push the module to the Buf Schema Registry**:
   ```bash
   buf push
   ```

## **Contributing**
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a feature branch.
3. Submit a pull request with a detailed description of your changes.

## **License**
This project is licensed under the MIT License. See `LICENSE` for details.

## **Contact**
For questions, suggestions, or support, open an issue on the GitHub repository.