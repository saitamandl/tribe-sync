# Database
## Naming Convention
Using `underscore_names` instead of `CamelCase` reduces ambiguity as SQL is case-insensitive.

- Table
  -
  - Plural table names avoid conflict with reserved keywords. For example, `user` table can conflict with SQL reserved word `user`. 
- Column
  - 
  - column name should be descriptive. For example, instead of `name` use `first_name` and `last_name`. Additionally, using `display_name` reduces ambiguity. 
  - `id` fields (`user_id` instead of `id`).
  - Don't use ambiguous column names (`euro` instead of `money_amount`).
  - When possible, name foreign key columns the same as the columns they refer to.