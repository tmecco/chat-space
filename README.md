# README
## group_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, |
### Association
- has_many :groups_users
- has_many :users, through:groups_users
- has_many :messages

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|index:true,null: false, unique: true|
|email|string|null: false, unique: true|
|pass|string|null:false|

### Association
- has_many :groups_users
- has_many :groups, through:groups_users
- has_many :messages

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|content|string|-------|
|image|string|-------|
|group|references|null: false, foreign_key: true|
|user|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user