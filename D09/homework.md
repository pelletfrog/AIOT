# 作業

## 作業1

* 安裝 Anaconda，使用 pip 或是 conda 工具安裝 pymongo 套件。
* Ans: 已安裝 Anaconda，並安裝 pymongo 套件


## 作業2

* 使用 python 操作 mongo 資料庫，包含新增、刪除、修改、查詢。
* Ans:
	* 開啟 mongo db
	* IDE - 連線、新增、查看

	```
	from pymongo import MongoClient
	client = MongoClient(host='127.0.0.1', port=8088)
	db = client.test
	collection = db.user

	mydata = {'name': 'pyname', 'tel': '123456'}
	result = collection.insert_one(mydata)
	print(result.inserted_id)

	result = collection.find()
	for x in result:
	    print(x)
	```

	* IDE - 新增多筆、查看

	```
	data_list = [
		{'name': 'pyname2', 'tel': '234567'},
		{'name': 'pyname3', 'tel': '334567'},
		{'name': 'pyname4', 'tel': '434567'},
		{'name': 'pyname5', 'tel': '534567'},
	]
	result = collection.insert_many(data_list)
	result.inserted_ids

	result = collection.find()
	for x in result:
	    print(x)
	```

	* IDE - 刪除一筆

	```
	// 查看集合中有多少文檔
	collection.count_documents({})

	// 刪除一個文檔
	collection.delete_one({})

	collection.count_documents({})

	collection.delete_one({'name': 'pyname3'})
	```

	* IDE - 刪除多筆

	```
	data_list = [
		{'name': 'pyname6', 'tel': '123'},
		{'name': 'pyname7', 'tel': '123'},
	]

	result = collection.insert_many(data_list)

	result = collection.delete_many({'tel': '123'})

	// 顯示刪除幾筆資料
	result.deleted_count
	```

	* IDE - 修改資料

	```
	// 過濾條件
	filter_ = {'name': 'pyname2'}

	// 要修改的資料部分
	update_ = {"$set": {"name": "pyname22"}}

	collection.update_one(filter_, update_)
	```

	* IDE - 修改多筆

	```
	filter_ = {'name': 'pyname3'}

	update_ = {"$set": {"name": "pyname33"}}

	collection.update_many(filter_, update_)
	```

	* IDE - 查詢資料

	```
	// 把找到的結果放進 result
	result = collection.find_one()

	// 印出結果
	result
	```

	* IDE - 查詢所有資料

	```
	result = collection.find()

	for x in result:
	    print(x)
	```

	* IDE - 排序

	```
	// 1 為小到大，-1 為大道小
	result = collection.find().sort('age', 1)

	for x in result:
	    print(x)
	```

	* IDE - 限制資料筆數

	```
	result = collection.find().limit(2)

	for x in result:
	    print(x)
	```