# DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|add_index, null: false, unique: true|
### Association
- has_many :groups, through: :user_groups
- has_many :messages, through: :user_groups

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|string| |
|image|string| |
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|string|null: false, unique: true|
### Association
- has_many :users, through: :user_groups
- has_many :messages

## user_groupテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false|
|group_id|integer|null: false|
### Association
- belongs_to :user
- belongs_to :group