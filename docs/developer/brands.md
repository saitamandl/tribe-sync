# Brands

## User Story

- [User](./users.md) can create Brands which will be part of the central system
- All the created items will be visible by every user in the system

## Dev Story

Multiple brands can have the same [items](./items.md)/products.

The data specification is in the following [subsections](#Tables)

> [!CAUTION]
> Recheck all the datatypes if they are the correct RDBMS data type.

### Tables

Table specification: list of columns excluding the default [columns](./databse.md#Table Configuration).

#### `brands` Table

|  Column name  | Data Type | Additional Comment |
|:-------------:|:----------|:------------------:|
| `brand_name`  | String    |       unique       |
| `description` | String    |         -          |


#### `junction_items_brands`
Associative table for `items` and `brands`

|  Column name   | Data Type | Additional Comment |
|:--------------:|:----------|:------------------:|
| `fk_items_id`  | String    |    foreign_key     |
| `fk_brands_id` | String    |    foreign_key     |