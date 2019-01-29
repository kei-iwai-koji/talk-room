# データベース設計


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|e_mail|string|null: false, unique: true|
|comment|text| |
|twitter_id|string| |
|team|string| |

### Association
- has_many :members
- has_many :rooms, through: :members
- has_many :talks
- has_many :goods
- has_many :bads


## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|reference|foreign_key: true|
|room_id|reference|foreign_key: true|

### Association
- belongs_to :user
- belongs_to :room


## roomsテーブル

|Column|Type|Options|
|------|----|-------|
|title|string|null: false|
|detail|text| |
|owner|reference|foreign_key: true|

### Association
- has_many :members
- has_many :users, through: :members
- has_many :talks


## talksテーブル

|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|user_id|reference|foreign_key: true|
|room_id|reference|foreign_key: true|

### Association
- belongs_to :user
- belongs_to :room
- has_many :goods
- has_many :bads


## goodsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|reference|foreign_key: true|
|talk_id|reference|foreign_key: true|

### Association
- belongs_to :user
- belongs_to :talk


## badsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|reference|foreign_key: true|
|talk_id|reference|foreign_key: true|

### Association
- belongs_to :user
- belongs_to :talk
