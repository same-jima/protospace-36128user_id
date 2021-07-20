# テーブル設計

## usersテーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| name               | string | null: false |
| email              | string | null: false |
| password           | string | null: false |
| profile            | string | null: false |
| position           | string | null: false |
| occupation         | string | null: false |


### Association

- has_many :commentsテーブル
- has_many :prototypesテーブル、through: :commentsテーブル



## prototypesテーブル

| Column             | Type         | Options                          |
| ------------------ | ------------ | -------------------------------- |
| title              | string       | null: false                      |
| catch_copy         | string       | null: false                      |
| concept            | string       | null: false                      |
| user               | references   | null: false, foreign_key: true   |

### Association

- has_many :usersテーブル, through: :commentsテーブル
- has_many :commentsテーブル

## commentsテーブル

| Column             | Type         | Options                          |
| ------------------ | ------------ | -------------------------------- |
| text               | text         | null: false                      |
| user               | references   | null: false, foreign_key: true   |
| prototype          | references   | null: false, foreign_key: true   |

### Association

- belong_to :usersテーブル
- belong_to :prototypesテーブル