# 作業

## 作業1

* 實際安裝 gpiozero，先安裝 RPi.GPIO，再安裝 pigpio，觀察安裝過程系統顯示的訊息。比較直接啟動 raspi-config 的 interfacing 選項，透過啟動 Remote GPIO，直接安裝GPIOZero。
* Ans: 
	* 安裝 RPi.GPIO

	```
	apt update
	apt install python3-rpi.gpio
	```

	* 安裝 pigpio

	```
	sudo apt-get update
	sudo apt-get install pigpio python-pigpio python3-pigpio

	cd /home/pi
	wget https://github.com/joan2937/pigpio/archive/master.zip
	unzip master.zip
	cd pigpio-master
	make
	sudo make install

	cd /home/pi
	rm master.zip

	sudo apt install python-setuptools python3-setuptools

	# 測試
	./x_pigpio`
	```

	* 最後安裝 GPIOZero

	```
	pi@raspberrypi:~/Desktop $ pip3 install gpiozero
	Looking in indexes: https://pypi.org/simple, https://www.piwheels.org/simple
	Requirement already satisfied: gpiozero in /usr/lib/python3/dist-packages (1.5.1)

	```



## 作業2

* 實際練習 GPIOZero 控制 LED，確定單獨的 GPIO 控制 LED 亮跟暗交替閃爍完成，並且 PWM 控制 LED 明亮的完成後，嘗試依序改變led.value的值，分別設定 0.1, 0.3, 0.5, 0.7 觀察差異。
* Ans: 

```
from gpiozero import PWMLED
from time import sleep

led = PWMLED(17)

while True:
	led.value = 0.1
	sleep(1)
	led.value = 0.3
	sleep(1)
	led.value = 0.5
	sleep(1)
	led.value = 0.7
	sleep(1)
```


## 作業3

* 實際練習 GPIOZero 透過 Button 控制 LED，在按鈕的過程中，觀察實際按下按鈕的次數，LED 點亮的次數，是否一致。練習修改程式，讓按鈕按下是全亮，按鈕放開後是 30% 的亮度。
* Ans: 

```
from gpiozero import PWMLED, Button
from signal import pause

led = PWMLED(17)
button = Button(2)

def led_on():
	led.value = 1

def led_off():
	led.value = 0.3

button.when_pressed = led_on
button.when_released = led_off
pause()
```