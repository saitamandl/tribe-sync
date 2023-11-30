# User
## User Story
- User will be able to register and log in
- User will be able to change password
- User will be able to delete account
- User can create [group](./group.md)(s)
- User can create Multiple [Grocery](./groceries.md) lists
- User can add [expenses](/expenditure.md)

## Dev Story
User module requires a lot of data to be stored. The data will be saved under. All the data shouldn't be stored in one table. Therefore, multiple table is used based on the context.
> [!CAUTION] 
> Recheck all the datatypes are exact RDBMS data type.

### `user` Table
List of columns excluding the default [columns](docs/technical/databse.md#Table Configuration).

| Column name | Data Type | Additional Comment |
|:-----------:|:----------|:------------------:|
| `username`  | String    |       unique       |
| `password`  | String    |        md5         |
|   `email`   | String    |      unique        |

### `user_information` Table
