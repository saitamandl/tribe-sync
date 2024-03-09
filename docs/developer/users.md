# Users

## User Story

- User will be able to register and log in
- User will be able to change password
- User will be able to delete account
- User can create [group](./groups.md)(s)
- User can create Multiple [Grocery](./groceries.md) lists
- User can add [expenses](/expenditure.md)

## Dev Story

The data specification is in the following [subsections](#Tables)
> [!CAUTION]
> Recheck all the datatypes if they are the correct RDBMS data type.

### Tables

Table specification: list of columns excluding the default [columns](./databse.md#Table Configuration).

#### `users` Table

| Column name | Data Type | Additional Comment |
|:-----------:|:----------|:------------------:|
| `username`  | String    |       unique       |
| `password`  | String    |        md5         |
|   `email`   | String    |       unique       |

#### `user_information` Table
Other information of the users

| Column name  | Data Type | Additional Comment |
|:------------:|:----------|:------------------:|
| `first_name` | String    |         -          |
| `last_name`  | String    |         -          |
|  `relation`  | String    |         -          |
| `fk_user_id` | String    |    foreign_key     |

#### `junction_users_groups`
Associative table for `users` and `groups`

|  Column name   | Data Type | Additional Comment |
|:--------------:|:----------|:------------------:|
| `fk_groups_id` | String    |    foreign_key     |
| `fk_users_id`  | String    |    foreign_key     |

#### `junction_users_elements`
Associative table for `users` and `elements`/modules 
Which will determine which user has permission to do what.

|   Column name    | Data Type | Additional Comment |
|:----------------:|:----------|:------------------:|
| `fk_elements_id` | String    |    foreign_key     |
|  `fk_users_id`   | String    |    foreign_key     |