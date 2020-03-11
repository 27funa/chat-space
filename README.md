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

# DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index|
|mail|string|null: false, unique: true|
|password|string|null: false, unique: true|

### Association
- has_many :posts
- has_many :users_groups
- has_many :groups, through: :users_groups

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|

### Association
- has_many :posts
- has_many :users_groups
- has_many :users, through: :users_groups

## users_groupsテーブル（中間テーブル users-groups）
|Column|Type|Options|
|------|----|-------|
|user_id|int|foreign_key: true|
|group_id|int|foreign_key: true|

### Association
- belong_to :user
- belong_to :group

## postsテーブル（message）
|Column|Type|Options|
|------|----|-------|
|text|text|-------|
|image|string|-------|
|user_id|int|foreign_key: true|
|group_id|int|foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group


