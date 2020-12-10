# テーブル設計



## users テーブル
| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| email              | string | null: false |
| encrypted_password | string | null: false |
| nickname           | string | null: false |
| last_name          | string | null: false |
| first_name         | string | null: false |
| last_name_kana     | string | null: false |
| first_name_kana    | string | null: false |
| birth_date         | date   | null: false |

### Association

- has_one  :career
- has_many :orders
- has_many :users_notes
- has_many :notes, through: :users_notes




## chefs テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| email              | string | null: false |
| encrypted_password | string | null: false |
| first_name         | string | null: false |
| last_name          | string | null: false |
| first_name_kana    | string | null: false |
| last_name_kana     | string | null: false |

### Association

- has_one  :career
- has_many :orders
- has_many :chefs_restaurants
- has_many :restaurants, through: :chef_restaurants
- has_many :notes




## restaurants テーブル
| Column        | Type    | Options     |
| ------------- | ------- | ----------- |
| image         |         |             |
| name          | string  | null: false |
| address       | string  | null: false |
| average_price | string  | null: false |
| info          | text    | null: false |
| employment_id | integer | null: false |
| occupation    | string  | null: false |
| shift         | string  | null: false |
| holiday       | string  | null: false |
| salary        | string  | null: false |
| genre_id      | integer | null: false |
| treatment     | text    | null: false |
| statue        | text    | null: false |

### Association

- has_many :chefs_restaurants
- has_many :chefs, through: chef_restaurants





## chef_restaurants テーブル
| Column        | Type       | Options           |
| ------------- | ---------- | ----------------- |
| chef_id       | references | foreign_key: true |
| restaurant_id | references | foreign_key: true |
|               |            |                   |

### Association

- belongs_to :chef
- belongs_to :restaurant




## notes テーブル
| Column | Type    | Options     |
| ------ | ------- | ----------- |
| title  | string  | null: false |
| info   | text    | null: false |
| price  | integer | null: false |

### Association
- belongs_to :chef
- has_one    :order
- has_many   :users_notes
- has_many   :users, through: :users_notes






## orders テーブル
| Column  | Type       | Options           |
| ------- | ---------- | ----------------- |
| user_id | references | foreign_key: true |
| chef_id | references | foreign_key: true |
| note_id | references | foreign_key: true |

### Association

- belongs_to :user
- belongs_to :chef
- belongs_to :note