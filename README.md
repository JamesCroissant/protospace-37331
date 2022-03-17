# テーブル設計

## usersテーブル

| Column             | Type   | Options                    |
| ------------------ | ------ | -------------------------- |
| email              | string | nulls: false, unique: false|
| encrypted_password | string | nulls: false               |
| name               | string | nulls: false               |
| profile            | text   | nulls: false               |
| occupation         | text   | nulls: false               |
| position           | text   | nulls: false               |

### Association

- has_many :prototypes, through: :comments
- has_many :comments


## commentsテーブル

| Column    | Type       | Options                         |
| --------- | ---------- | ------------------------------- |
| content   | text       | nulls: false                    |
| prototype | references | nulls: false, foreign_key: true |
| user      | references | nulls: false, foreign_key: true |


### Association

- belongs_to :users
- belongs_to :prototypes


## prototypesテーブル

| Column     | Type       | Options                         |
| ---------- | ---------- | ------------------------------- |
| title      | string     | nulls: false                    |
| catch_copy | text       | nulls: false                    |
| concept    | text       | nulls: false                    |
| user       | references | nulls: false, foreign_key: true |


### Association

- has_many :users, through: :comments
- has_many :comments