# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|username|string|null: false, unique:true|
|email|string|null: false|
|passward|string|null: false|
### Association
- has_many :messages
- has_many :groups, 


## groupsテーブル
Column|Type|Options|
|------|----|-------|
|groupname|string|null: false|
|user_id|integer|null: false|
### Association
- has_many :messages
- has_many :groups
- has_many :users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|body|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## messages_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|message_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :message
- belongs_to :user

## messages_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false, foreign_key: true|
|message_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :message
- belongs_to :group