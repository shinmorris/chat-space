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

# chatspace DB設計
## usersテーブル
|name|email|password|
|----|-----|--------|
|name|string|null: false|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many :groups
- has_many :group_members

## groupsテーブル
|group_name|chat_member|user_id|
|----------|-----------|-------|
|group_name|text|null: false|
|chat_member|text||
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- has_many :posts
- has_many :group_members

## group_memberテーブル
|user_id|group_id|
|-------|-----|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## postsテーブル
|message|image|group_id|
|-------|-----|--------|
|message|text|null: false|
|image|text|null: false|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
