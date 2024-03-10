# Items

## User Story

- [User](./users.md) can create Items which will be part of the central system
    - Items can have [brands](./brands.md)
- Item name has to be unique
- All the created items will be visible by every user in the system

## Dev Story

[Grocery](./grocery_lists) lists will be consists of items

- Item will be linked to where (Penny/Edeka) is it bought from
    - Item can be linked to multiple supermarket
- What brand is it from
    - Item can multiple brands
- Item will have type
    - e.g. vegetable or meat or fish based on the supermarket category

The data specification is in the following [subsections](#Tables)

> [!CAUTION]
> Recheck all the datatypes if they are the correct RDBMS data type.

### Tables

Table specification: list of columns excluding the default [columns](./databse.md#Table Configuration).

#### `items` Table

|  Column name  | Data Type | Additional Comment |
|:-------------:|:----------|:------------------:|
|  `item_name`  | String    |       unique       |
|  `category`   | String    |         -          |
| `description` | String    |         -          |

#### `items_locale` Table
Contains translations for the items

| Column name | Data Type |     Additional Comment     |
|:-----------:|:----------|:--------------------------:|
|  `item_id`  | String    |        foreign_key         |
| `item_name` | String    | combine-unique with locale | 
|  `locale`   | String    |         e.g. en/de         |

#### `junction_items_brands`

Associative table for `items` and `brands`

|  Column name   | Data Type | Additional Comment |
|:--------------:|:----------|:------------------:|
| `fk_items_id`  | String    |    foreign_key     |
| `fk_brands_id` | String    |    foreign_key     |