# Database
## Convention
### Naming
Using `underscore_names` instead of `CamelCase` reduces ambiguity as SQL is case-insensitive.

#### Table
Break down the data in multiple table based on context. For example, `user` table shouldn't have personal information like `last_name` and `first_name`. `user_information` or `personal_information` table should be used to store `last_name` and `first_name`. 

table names should be plural to avoid conflict with reserved keywords. For example, `user` table can conflict with SQL reserved word `user`. 
#### Column
  Column name should be descriptive. For example, instead of `name` use `first_name` and `last_name`. Additionally, using `display_name` reduces ambiguity. 
  - `id` fields (`user_id` instead of `id`).
  - Don't use ambiguous column names (`euro` instead of `money_amount`).
  - When possible, name foreign key columns the same as the columns they refer to.
### Table Configuration
All the table should contain the following columns.

|          Column name          | Data Type |         Additional Comment          |
|:-----------------------------:|:----------|:-----------------------------------:|
|         `{table}_id`          | String    | `unique_id`-> primary key; not null |
|   `created_on_{time_zone}`    | Time      |              not null               |
| `last_updated_on_{time_zone}` | Time      |                                     |
|         `created_by`          | String    | `user_id` -> foreign key; not null  |
|       `last_updated_by`       | String    | `user_id` -> foreign key; not null  |
|          `is_enable`          | boolean   |              optional               |