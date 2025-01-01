# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [postgres/v1/postgres_options.proto](#postgres_v1_postgres_options-proto)
    - [AdvancedColumnProperties](#postgres-v1-AdvancedColumnProperties)
    - [ColumnProperties](#postgres-v1-ColumnProperties)
    - [ExclusionConstraint](#postgres-v1-ExclusionConstraint)
    - [Grant](#postgres-v1-Grant)
    - [IndexDefinition](#postgres-v1-IndexDefinition)
    - [Partitioning](#postgres-v1-Partitioning)
    - [TableProperties](#postgres-v1-TableProperties)
    - [TableProperties.PropertiesEntry](#postgres-v1-TableProperties-PropertiesEntry)
  
    - [ColumnConstraint](#postgres-v1-ColumnConstraint)
    - [ForeignKeyAction](#postgres-v1-ForeignKeyAction)
    - [IndexType](#postgres-v1-IndexType)
    - [Partitioning.Type](#postgres-v1-Partitioning-Type)
  
    - [File-level Extensions](#postgres_v1_postgres_options-proto-extensions)
    - [File-level Extensions](#postgres_v1_postgres_options-proto-extensions)
    - [File-level Extensions](#postgres_v1_postgres_options-proto-extensions)
    - [File-level Extensions](#postgres_v1_postgres_options-proto-extensions)
  
- [Scalar Value Types](#scalar-value-types)



<a name="postgres_v1_postgres_options-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## postgres/v1/postgres_options.proto



<a name="postgres-v1-AdvancedColumnProperties"></a>

### AdvancedColumnProperties
=============================
Advanced Properties
=============================


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| generated_column | [bool](#bool) |  | Generated column. |
| identity_column | [bool](#bool) |  | Identity column. |
| deferrable | [bool](#bool) |  | Deferrable constraint. |
| initially_deferred | [bool](#bool) |  | Initially deferred constraint. |






<a name="postgres-v1-ColumnProperties"></a>

### ColumnProperties
=============================
Column-Level Properties
=============================


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| column_type | [string](#string) |  | PostgreSQL data type for the column. |
| constraints | [ColumnConstraint](#postgres-v1-ColumnConstraint) | repeated | Column constraints (e.g., PRIMARY KEY, NOT NULL). |
| default_value | [string](#string) |  | Default value for the column. |
| foreign_key | [string](#string) |  | Foreign key reference (table.column). |
| on_delete | [ForeignKeyAction](#postgres-v1-ForeignKeyAction) |  | Action on delete. |
| on_update | [ForeignKeyAction](#postgres-v1-ForeignKeyAction) |  | Action on update. |






<a name="postgres-v1-ExclusionConstraint"></a>

### ExclusionConstraint
=============================
Exclusion Constraint
=============================


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Constraint name. |
| expression | [string](#string) |  | Expression or column involved. |
| operator | [string](#string) |  | Exclusion operator (e.g., &#34;WITH &amp;&amp;&#34;). |
| index_type | [IndexType](#postgres-v1-IndexType) |  | Index type for the constraint. |






<a name="postgres-v1-Grant"></a>

### Grant
=============================
Permissions and Grants
=============================


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| privilege | [string](#string) |  | Privilege type (e.g., SELECT, INSERT). |
| role | [string](#string) |  | Role receiving the privilege. |






<a name="postgres-v1-IndexDefinition"></a>

### IndexDefinition
=============================
Index Definition
=============================


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | Index name. |
| columns | [string](#string) | repeated | Columns included in the index. |
| expression | [string](#string) |  | Expression for expression-based indexes. |
| index_type | [IndexType](#postgres-v1-IndexType) |  | Index type. |
| unique | [bool](#bool) |  | Unique index. |
| where_clause | [string](#string) |  | Partial index condition. |






<a name="postgres-v1-Partitioning"></a>

### Partitioning
=============================
Partitioning Definition
=============================


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| type | [Partitioning.Type](#postgres-v1-Partitioning-Type) |  | Partitioning type. |
| keys | [string](#string) | repeated | Partitioning keys. |






<a name="postgres-v1-TableProperties"></a>

### TableProperties
=============================
Table-Level Properties
=============================


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| table_name | [string](#string) |  | PostgreSQL table name. |
| schema | [string](#string) |  | Schema for the table. |
| properties | [TableProperties.PropertiesEntry](#postgres-v1-TableProperties-PropertiesEntry) | repeated | General table properties (e.g., autovacuum settings). |
| indexes | [IndexDefinition](#postgres-v1-IndexDefinition) | repeated | Table indexes. |
| partitioning | [Partitioning](#postgres-v1-Partitioning) |  | Partitioning details. |
| grants | [Grant](#postgres-v1-Grant) | repeated | Permissions or grants for the table. |
| exclusions | [ExclusionConstraint](#postgres-v1-ExclusionConstraint) | repeated | Exclusion constraints. |






<a name="postgres-v1-TableProperties-PropertiesEntry"></a>

### TableProperties.PropertiesEntry



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| key | [string](#string) |  |  |
| value | [string](#string) |  |  |





 


<a name="postgres-v1-ColumnConstraint"></a>

### ColumnConstraint
=============================
Column Constraint Enum
=============================

| Name | Number | Description |
| ---- | ------ | ----------- |
| COLUMN_CONSTRAINT_UNSPECIFIED | 0 |  |
| COLUMN_CONSTRAINT_PRIMARY_KEY | 1 |  |
| COLUMN_CONSTRAINT_NOT_NULL | 2 |  |
| COLUMN_CONSTRAINT_UNIQUE | 3 |  |
| COLUMN_CONSTRAINT_CHECK | 4 |  |
| COLUMN_CONSTRAINT_FOREIGN_KEY | 5 |  |



<a name="postgres-v1-ForeignKeyAction"></a>

### ForeignKeyAction
=============================
Foreign Key Action Enum
=============================

| Name | Number | Description |
| ---- | ------ | ----------- |
| FOREIGN_KEY_ACTION_UNSPECIFIED | 0 |  |
| FOREIGN_KEY_ACTION_RESTRICT | 1 |  |
| FOREIGN_KEY_ACTION_CASCADE | 2 |  |
| FOREIGN_KEY_ACTION_SET_NULL | 3 |  |
| FOREIGN_KEY_ACTION_SET_DEFAULT | 4 |  |



<a name="postgres-v1-IndexType"></a>

### IndexType
=============================
Index Type Enum
=============================

| Name | Number | Description |
| ---- | ------ | ----------- |
| INDEX_TYPE_UNSPECIFIED | 0 |  |
| INDEX_TYPE_BTREE | 1 |  |
| INDEX_TYPE_GIN | 2 |  |
| INDEX_TYPE_GIST | 3 |  |
| INDEX_TYPE_HASH | 4 |  |



<a name="postgres-v1-Partitioning-Type"></a>

### Partitioning.Type


| Name | Number | Description |
| ---- | ------ | ----------- |
| TYPE_UNSPECIFIED | 0 |  |
| TYPE_RANGE | 1 |  |
| TYPE_HASH | 2 |  |
| TYPE_LIST | 3 |  |


 


<a name="postgres_v1_postgres_options-proto-extensions"></a>

### File-level Extensions
| Extension | Type | Base | Number | Description |
| --------- | ---- | ---- | ------ | ----------- |
| advanced_column_properties | AdvancedColumnProperties | .google.protobuf.FieldOptions | 55000 | Advanced properties. |
| column_properties | ColumnProperties | .google.protobuf.FieldOptions | 51000 | Custom column properties. |
| is_composite_type | bool | .google.protobuf.MessageOptions | 58000 | Marks the message as a composite type. |
| table_properties | TableProperties | .google.protobuf.MessageOptions | 50000 | Custom table properties. |

 

 



## Scalar Value Types

| .proto Type | Notes | C++ | Java | Python | Go | C# | PHP | Ruby |
| ----------- | ----- | --- | ---- | ------ | -- | -- | --- | ---- |
| <a name="double" /> double |  | double | double | float | float64 | double | float | Float |
| <a name="float" /> float |  | float | float | float | float32 | float | float | Float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum or Fixnum (as required) |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="bool" /> bool |  | bool | boolean | boolean | bool | bool | boolean | TrueClass/FalseClass |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode | string | string | string | String (UTF-8) |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str | []byte | ByteString | string | String (ASCII-8BIT) |

