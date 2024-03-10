# Grocery Lists

## User Story

- [User](./users.md) can create Multiple grocery lists for personal or as part of [groups](./groups.md)
  - Grocery lists consist of [items](./items.md)
- Grocery lists will be visible to all the user in the group and will be able to check off items of the list
- Only an authorised user can add/remove new item in the list
- An authorised user can deactivate grocery lists
- An authorised user can Permanently delete grocery lists


## Dev Story
The data specification is in the following [subsections](#Tables)

> [!CAUTION]
> Recheck all the datatypes if they are the correct RDBMS data type.

### Tables

Table specification: list of columns excluding the default [columns](./databse.md#Table Configuration).

#### `grocery_lists` Table

|      Column name      | Data Type | Additional Comment |
|:---------------------:|:----------|:------------------:|
|  `grocery_list_name`  | String    |       unique       |
|     `description`     | String    |         -          |

#### `junction_grocery_lists_items`
Associative table for `grocery_list` and `items`

|     Column name      | Data Type | Additional Comment |
|:--------------------:|:----------|:------------------:|
| `fk_grocery_list_id` | String    |    foreign_key     |
|    `fk_items_id`     | String    |    foreign_key     |
|   `grocery_status`   | String    | un/checked/skipped |