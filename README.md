# README

URL http://18.178.119.38/
ID/Pass
ID: team72a
Pass: 2222


テスト用アカウント等
購入者用
メールアドレス: purchase72a@mail.com
パスワード: 1234567


購入用カード情報
番号：4242424242424242
期限：12/20
セキュリティコード：123


出品者用
メールアドレス名:  sell72a@mail.com
パスワード: 7654321


# freemarket_sample_72a DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|email|string|null: false, unique: true|
|password|string|null: false|
|phone_number|string|null: false, unique: true, index: true|
|first_name|string|null: false|
|last_name|string|null: false|
|first_name_reading|string|null: false|
|last_name_reading|string|null: false|
|birthday_year|string|null: false|
|birthday_month|string|null: false|
|birthday_day|string|null: false|
### association
- has_one :deliver_address
- has_many :orders
- has_many :cards
- has_many :items

## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|price|integer|null: false|
|condition|string|null: false|
|description|text|null: false|
|size|string|null: false|
|ship_area|string|null: false|
|ship_day|string|null: false|
|ship_price|string|null: false|
|ship_method|string|null: false|
|user_id|references|null: false, foreign_key: true|
|category_id|references|null: false, foreign_key: true|
|brand_id|references|null: false, foreign_key: true|
### association
- belongs_to :user
- belongs_to :category
- belongs_to :brand
- has_many :orders
- has_many :item_images

## deliver_addressesテーブル
|Column|Type|Options|
|------|----|-------|
|first_name|string|null: false|
|last_name|string|null: false|
|first_name_reading|string|null: false|
|last_name_reading|string|null: false|
|post_code|string|null: false|
|prefecture_id|integer|null: false|
|address_city|string|null: false|
|address_street|string|null: false|
|address_building|string||
|phone_number|string||
|user_id|references|null: false, foreign_key: true|
### association
- belongs_to :user
- has_many :orders

## item_imagesテーブル
|Column|Type|Options|
|------|----|-------|
|image_url|string|null: false|
|item_id|references|null: false, foreign_key: true|
### association
- belongs_to :item

## categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|ancestry|string||
### association
- has_many :items

## brandsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique:true|
### association
- has_many :items

## cardsテーブル
|Column|Type|Options|
|------|----|-------|
|card_id|string|null: false|
|customer_id|string|null: false|
|user_id|references|null: false, foreign_key: true|
### association
- belongs_to :user
