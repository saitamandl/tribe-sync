# Groups

## User Story

- Groups can be created
- Groups can have password set by admin [User](./users.md)
- Groups can be deleted
- Groups can have multiple [Grocery](./groceries.md) lists
- Groups can have [expenses](/expenditure.md)

## Dev Story
A default group name `personal` will be created for Every user. All the grocery lists and expenses has to be part of a group.

The data specification is in the following [subsections](#Tables)

> [!CAUTION]
> Recheck all the datatypes if they are the correct RDBMS data type.

### Tables

Table specification: list of columns excluding the default [columns](./databse.md#Table Configuration).

#### `groups` Table

|  Column name  | Data Type | Additional Comment |
|:-------------:|:----------|:------------------:|
|  `groupname`  | String    |       unique       |
|  `password`   | String    |   md5 / optional   |
| `description` | String    |         -          |

#### `junction_users_groups`

Associative table for `users` and `groups`

|  Column name   | Data Type | Additional Comment |
|:--------------:|:----------|:------------------:|
| `fk_groups_id` | String    |    foreign_key     |
| `fk_groups_id` | String    |    foreign_key     |

#### `junction_groups_groceries`

Associative table for `groups` and `groceries`

|    Column name    | Data Type | Additional Comment |
|:-----------------:|:----------|:------------------:|
| `fk_groceries_id` | String    |    foreign_key     |
|  `fk_groups_id`   | String    |    foreign_key     |

#### `junction_groups_expenses`

Associative table for `groups` and `expenses`

|   Column name    | Data Type | Additional Comment |
|:----------------:|:----------|:------------------:|
| `fk_expenses_id` | String    |    foreign_key     |
|  `fk_groups_id`  | String    |    foreign_key     |

