# テーブル設計

## users テーブル

| Column           | Type   | Options     |
| ---------------- | ------ | ----------- |
| nickname         | string | null: false |
| email            | string | null: false |
| password         | string | null: false |
| family_name      | string | null: false |
| first_name       | string | null: false |
| family_name_kana | string | null: false |
| first_name_kana  | string | null: false |
| date_of_birth    | date   | null: false |
### Association

- has_many :items 
- has_many :purchase
- has_one  :items, through: :managements

## items テーブル

| Column             |  Type      | Options                         |
| ------------------ | ---------- | ------------------------------- |
| name               | string     | null: false                     |
| image              | string     | null: false                     |
| explain            | string     | null: false                     |
| category           | integer    | null: false                     |
| statas             | integer    | null: false                     |
| delivery_fee       | integer    | null: false                     |
| place_for_delivery | integer    | null: false                     |
| date_for_delivery  | integer    | null: false                     |
| price              | string     | null: false                     |
| user               | references | null: false, foreign_key: true  |

### Association

- belongs_to :user
- has_one    :purchase
- has_one    :users, through: :managements

## purchases テーブル

| Column           | Type       | Options                         |
| ---------------- | ---------- | ------------------------------- |
| user             | references | null: false, foreign_key: true  |
| item             | references | null: false, foreign_key: true  |
| card_information | string     | null: false                     |
| security_code    | string     | null: false                     |
| comment          | string     | null: false                     |

### Association

- belongs_to :user
- belongs_to :item
- has_one_to :adress

## managements テーブル

| Column           | Type       | Options                         |
| ---------------- | ---------- | ------------------------------- |
| user             | references | null: false, foreign_key: true  |
| item             | references | null: false, foreign_key: true  |

### Association

- belongs_to :user
- belongs_to :item

## adress テーブル

| Column       |  Type      | Options                         |
| ------------ | ---------- | ------------------------------- |
| postal_code  | integer    | null: false                     |
| prefecture   | integer    | null: false                     |
| city         | integer    | null: false                     |
| street       | integer    | null: false                     |
| building     | integer    | null: false                     |
| phone number | integer    | null: false                     |
| purchase     | references | null: false, foreign_key: true  |

### Association

- belongs_to :purchase