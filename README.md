# テーブル設計

## users テーブル

| Column        | Type   | Options     |
| ------------- | ------ | ----------- |
| nickname      | string | null: false |
| email         | string | null: false |
| password      | string | null: false |
| name          | string | null: false |
| date_of_birth | string | null: false |
### Association

- has_many :items
- has_one  :purchase

## items テーブル

| Column   |  Type      | Options                         |
| -------- | ---------- | ------------------------------- |
| name     | string     | null: false                     |
| image    | string     | null: false                     |
| explain  | string     | null: false                     |
| detail   | string     | null: false                     |
| category | string     | null: false                     |
| statas   | string     | null: false                     |
| price    | string     | null: false                     |
| user     | references | null: false, foreign_key: true  |

### Association

- belongs_to :user
- has_one    :purchase

## purchases テーブル

| Column           | Type       | Options                         |
| ---------------- | ---------- | ------------------------------- |
| user             | references | null: false, foreign_key: true  |
| item             | references | null: false, foreign_key: true  |
| address          | string     | null: false                     |
| card_information | string     | null:false                      |
| comment          | string     | null: false                     |

### Association

- belongs_to :user
- belongs_to :item