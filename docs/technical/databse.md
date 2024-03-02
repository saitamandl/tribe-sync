# Database

## Convention

### Naming

Using `underscore_names` instead of `CamelCase` reduces ambiguity as SQL is case-insensitive.

#### Table

Break down the data in multiple table based on context. For example, `user` table shouldn't have personal information
like `last_name` and `first_name`. `user_information` or `personal_information` table should be used to
store `last_name` and `first_name`.

Table names should be plural to avoid conflict with reserved keywords. For example, `user` table can conflict with SQL
reserved word `user`.

Associative tables, holds associations of multiple table, should have a prefix `junktion_{table1}_{table2}` as it
is a junction for tables with many to many relationship. e.g. `junction_users_groups`

#### Column

Column name should be descriptive. For example, instead of `name` use `first_name` and `last_name`. Additionally,
using `display_name` reduces ambiguity.

- `id` fields (`{table}_id` instead of `id`).
- Primary key should have a prefix `pk_` (`pk_{table}_id` instead of `{table}_id`)
- Don't use ambiguous column names (`euro` instead of `money_amount`).
- When possible, name foreign key columns the same as the columns they refer to.
    - Foreign key should have a prefix `fk_` (`fk_{foreign_table}_id` instead of `pk_{foreign_table}_id`)

### Table Configuration

All the table should contain the following columns.

|          Column name          | Data Type |          Additional Comment           |
|:-----------------------------:|:----------|:-------------------------------------:|
|        `pk_{table}_id`        | String    |  `unique_id`-> primary key; not null  |
|   `created_on_{time_zone}`    | Time      |               not null                |
| `last_updated_on_{time_zone}` | Time      |                                       |
|         `created_by`          | String    | `pk_user_id` -> foreign key; not null |
|       `last_updated_by`       | String    | `pk_user_id` -> foreign key; not null |
|          `is_enable`          | boolean   |               optional                |

### Tools

- [Liquibase](https://www.liquibase.org/) will be used to provide multi RDBMS support.