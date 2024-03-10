# Groups

## User Story

- Groups can be created 
- Group name has to be unique per group
- Groups can have password set by an [admin](./users.md)
- Groups can have multiple [Grocery](./grocery_lists) lists
- Groups can have [expenses](/expenditure.md)
- Permission:
  - Groups
    - Admin will have the ability to choose which users in the group can
      - Add/change password of the group
      - Update group name/description
      - Deactivate group
      - Permanently delete the group
      - Deactivated groups will be visible by all the groups members in the deactivated tab of the user
  - Grocery lists
    - Grocery lists will be visible to all the user in the group and will be able to check off items of the lists
    - Admin will have the ability to choose which users in the group can
      - Create grocery lists
      - Add/remove new item in the lists
      - Deactivate grocery lists
      - Permanently delete grocery lists
      - Deactivated grocery lists will be visible by all the groups members in the deactivated tab of the group
    
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
|  `groupname`  | String    |  unique per group  |
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

