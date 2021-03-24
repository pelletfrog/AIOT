# 作業

## 作業1

* 安裝 MongoDB、 Robo 3T 工具。
* Ans: 已皆安裝


## 作業2

* 分別使用指令、Robo 3T 操作 Mongo 資料庫。
* Ans: 
	* 建立 Member db `use Member`
	* 建立 Member collection 並塞入資料 `db.Member.insert({"name": "Kevin", "email": "test@abc.com", "phone": "0912345678"});`，完成系統回傳 `回傳WriteResult({ "nInserted" : 1 })`
	* 查詢 `db.Member.find()`，可看到新增的資料 `{ "_id" : ObjectId("605aced78f77bfd3878649dc"), "name" : "Kevin", "email" : "test@abc.com", "phone" : "0912345678" }`
	* 更新增加 age `db.Member.update({"_id": ObjectId("605aced78f77bfd3878649dc")}, {$set: {"age" : 25}})`，成功回傳 `WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })`
	* 再次查詢 `db.Member.find()`，可看到 `{ "_id" : ObjectId("605aced78f77bfd3878649dc"), "name" : "Kevin", "email" : "test@abc.com", "phone" : "0912345678", "age" : 25 }`