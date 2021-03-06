# Mongo DB
I am a first time user of mongo db, so I am going to note down all commands I'll need to use again and again. You can start mongo admin on shell as:

```php
> mongo admin

# show mostly used mongo commands using help
> help
```

* Show Databases

```php
# Print a list of all databases on the server.
> show dbs
// or
> show databases
```

* Use Database

```php
# Switch current database to <db>. The mongo shell variable db is set to the current database.
> use <dbname>
```

* Show Collections / Tables

```php
# Print a list of all collections for current database
> show collections
// or
> show tables
```

* insert into db.collections
```php
# use dbname
> use myproject

# insert one row
> db.trademe_photos.insert({name: 'image1.jpg', data: 'data 1 goes here', md5: '1sjdhfjhjf'}) 

# inserts multiple rows
> db.trademe_photos.insert(
[
  {name: 'image2.jpg', data: 'data 2 goes here', md5: '2sjdhfjhjf'},
  {name: 'image3.jpg', data: 'data 3 goes here', md5: '3sjdhfjhjf'}
]
) 
```

* Select * from db.collections
```php
# use dbname
> use myproject

# trademe_photos is a collection inside db 'myproject'
> db.trademe_photos.find() 

# prettify result
> db.trademe_photos.find().pretty() 
```

* select * from db.collection where column/field doesn't exists or has defined value
* Get rows if listingId doesn't exists or has value 0 or less.
```php
db.trademe_listings.find({expired:0, $or:[{listingId:{$exists: false}}, {listingId:{$lte:0}}]})
```

* Select * from db.collections where md5="4sjdhfjhjf"
```php
> db.trademe_photos.findOne({md5:'4sjdhfjhjf'})
```

* find * from db.collection sort by field/column 'lowesSize' in Ascending Order. NOTE: double bracket **[[..]]**
```php
var cursor = db.collection(MongoDB.collections.listings).find({}, {"sort" : [['lowesSize', 'asc']]});
```

* Update table set (new data) where md5="4sjdhfjhjf"
```php
> db.trademe_photos.update(
	{md5:'4sjdhfjhjf'},
	{
		$set:
		{
			name: 'image4a.jpg', 
			data:'sdhfjsd/=', 
			md5:'4akjshfdjsh'
		}
	}
)
// @link https://docs.mongodb.com/manual/reference/operator/update-field/
```
