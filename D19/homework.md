# 作業

## 作業1

* 利用GPIO 控制風扇
	* 選擇 GPIO 做控制
	* 設定供電與接地管腳 define
* 電源和接地管腳
	* 電源和接地管腳用於為外部電路供電。
	* 所有帶有標準 40 GPIO 引腳的 Raspberry Pi 都將有兩個 5V 引腳和兩個 3.3V 引腳，且始終位於同一位置。
* Ans:
	* 因沒有電扇，改用 led 與 webcam
	* python

	```python
	from flask import Flask, render_template, request
	import RPi.GPIO as GPIO
	import time
	import os

	app = Flask(__name__)

	# global
	led_pin = 2

	# Initial state for LEDs:
	try:
	  print("set GIOP")
	  GPIO.setmode(GPIO.BCM)
	  GPIO.setup(led_pin, GPIO.OUT)             
	except KeyboardInterrupt: # If CTRL+C is pressed, exit cleanly:
	  print("Keyboard interrupt")
	except:
	  print("some error") 
	finally:
	  # print("clean up") 
	  # GPIO.cleanup() # cleanup all GPIO
	  print("test test")

	@app.route("/", methods=['GET'])
	def main_index(): 
	  return render_template('index.html')

	@app.route("/on", methods=['GET'])
	def on():
	  GPIO.output(led_pin, True)
	  return "LED on"

	@app.route("/off", methods=['GET'])
	def off():
	  GPIO.output(led_pin, False)
	  return "LED off"

	@app.route("/shining", methods=['GET'])
	def shining():
	  while(True):
	      GPIO.output(led_pin, False)
	      time.sleep(1)
	      GPIO.output(led_pin, True)
	      time.sleep(1)
	  return "LED shining"

	@app.route("/photo", methods=["GET"])
	def photo():
	  os.system('fswebcam -r 320x240 -S 3 --jpeg 50 --save /home/flask/photo/%H%M%S.jpg')
	  return "photo"

	# GPIO.cleanup()

	if __name__ == "__main__":
	  app.run(host='0.0.0.0', port=8080, debug=True, threaded=True)
	```

	* index.html

	```html
	<!DOCTYPE html>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width,initial-scale=1">
	<!--Bootstrap-->
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.1/dist/css/bootstrap.min.css" integrity="sha384-zCbKRCUGaJDkqS1kPbPd7TveP5iyJE0EjAuZQTgFLD2ylzuqKfdKlfG/eSrtxUkn" crossorigin="anonymous">
	<script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
	<script src="https://cdn.jsdelivr.net/npm/bootstrap@4.6.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-fQybjgWLrvvRgtW6bFlB7jaZrFsaBXjsOMm/tB9LTS58ONXgqbR9W8oWht/amnpF" crossorigin="anonymous"></script>
	<style>
	a { width: 100%; }
	.col { margin-bottom: 10px; }
	</style>
	<head>
	<title>LED 燈開關</title>
	</head>
	<body>
	<div class="container-fluid">
	    <div class="row">
	        <div class="col">
	            <a href="/on" class="btn btn-success btn-lg" role="button">開</a>
	        </div>
	    </div>
	    <div class="row">
	        <div class="col">
	            <a href="/off" class="btn btn-success btn-lg" role="button">關</a>
	        </div>
	    </div>
	    <div class="row">
	        <div class="col">
	            <a href="/shining" class="btn btn-success btn-lg" role="button">閃爍</a>
	        </div>
	    </div>
	    <div class="row">
	        <div class="col">
	            <a href="/photo" class="btn btn-success btn-lg" role="button">拍照</a>
	        </div>
	    </div>
	</div>
	</body>
	</html>
	```