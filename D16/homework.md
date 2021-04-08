# 作業

## 作業1

* 從 Docker Hub 取得一個含有 Python、Flask 的映像檔，執行容器，並且可以從瀏覽器看到執行結果
* Ans: 
	* 進網址 <https://hub.docker.com/r/kurtliao/flask-demo>
	* 下載 `docker pull kurtliao/flask-demo`
	* 查看 `docker images`
	* 啟動 `docker run -p 5000:5000 --name flask-app kurtliao/flask-demo` (使用 docker run 指令，搭配參數 -p 指定port，讓外部可以連到 container 裡面的 flask server)
	* 開啟瀏覽器輸入 <http://0.0.0.0:5000/> 可看到 Hello World!
	* 開一新的 cmd 輸入 `docker ps -a` 可看到 status 為 up