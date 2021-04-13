# 作業

## 作業1

* 撰寫一個 Flask Web 應用程式，分別使用 Get / Post 來發送 Request，且能取得 Request 傳遞的參數。
* Ans: 
	* 使用 GET 取得 Request 中的參數 (測試：<http://127.0.0.1:5000?name=test>)

	```python
	# 引用需要的套件, 若有多個套件要引用，可使用逗號隔開
	from flask import Flask, request

	app = Flask(__name__)

	# 設定網址路由，及接受的 method(預設是 GET)
	@app.route('/', methods=['GET'])
	def index():
	    name = request.args.get('name') # 取得 name 參數
	    return "Hello " + name
	    
	if __name__ == '__main__':
	    app.run()
	```

	* 使用 Post 傳遞參數資料 (postman 設定 post http://127.0.0.1:5000, formdata, name: testname, passwd: testpasswd)

	```python
	# 引用需要的套件, 若有多個套件要引用，可使用逗號隔開
	from flask import Flask, request

	app = Flask(__name__)

	# 設定網址路由，及接受的 method(預設是 GET)
	@app.route('/', methods=['POST'])
	def index():
	    name = request.form.get('name') # 取得 name 參數
	    passwd = request.form.get('passwd') # 取得 passwd 參數
	    return "Your name: " + name + ", Your passwd: " + passwd

	if __name__ == '__main__':
	    app.run()
	```


## 作業2

* 實作檔案上傳功能，並提供簡易畫面使其能透過畫面上傳檔案。
	* 使用 Post 檔案上傳單一檔案 (postman 設定 post http://127.0.0.1:5000, formdata, file: 檔案)

	```python
	# 引用需要的套件, 若有多個套件要引用，可使用逗號隔開
	from flask import Flask, request

	app = Flask(__name__)

	# 設定網址路由，及接受的 method(預設是 GET)
	@app.route('/', methods=['POST'])
	def index():
	    file = request.files['file'] # 取得 request 中的 file(記得發送 postman 中的 檔案參數名稱要和這邊一致)
	    file.save(file.filename) # 把檔案存起來，並用原來的檔名作為名稱
	    
		return file.filename # 回傳檔案名稱
	    
	if __name__ == '__main__':
	    app.run()
	```