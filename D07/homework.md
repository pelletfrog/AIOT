# 作業

## 作業1

* 安裝 Docker，並從 Docker Hub 下載映像檔後建立容器
* Ans: 
	* 使用 `docker pull ubuntu` 下載 image
	* `docker images` 查詢可看到

	```
	REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
	httpd                     latest              ae15ff2bdcb4        10 days ago         138MB
	ubuntu                    latest              4dd97cefde62        2 weeks ago         72.9MB
	```

	* 建立 ubuntu container `docker run --name ubuntu-test ubuntu`
	* `lai$ docker ps -a` 查詢可看到

	```
	CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
	ef2252fa18be        ubuntu              "/bin/bash"              25 seconds ago      Exited (0) 24 seconds ago                       ubuntu-test
	```



## 作業2

* 連接本機端資料夾和容器中的資料夾
* Ans: 
	* 建立 `docker run -it -v /Users/ppp/Downloads/test:/var/test --name folder-test ubuntu bash`
	* `cd var` 與 `ls` 查看，可看到資料夾

	```
	backups  cache  lib  local  lock  log  mail  opt  run  spool  test  tmp
	```

	* `cd test` 並建立檔案 `touch test.txt`
	* 於本機下 `cd downloads/test`，`ls` 也可查看到檔案


## 作業3

* 使用 docker exec 指令進入到容器中，查看容器中資料夾和本地端的資料夾有確實互連
* Ans: 
	* 於本機的 /downloads/test 中再建立 test2.txt 檔案
	* `docker exec -it folder-test bash` 進入 container
	* 在於 container 中 `cd var/test` 並 `ls ` 可看到

	```
	test.txt  test2.txt
	```