# 作業

## 作業1

* 實際練習 /sys/class/gpio 啟動 gpio，設定 gpio 接腳的狀態，並且卸載所啟動的 gpio。同時觀察卸載之後的 gpio 接腳，繼續送設定狀態的資料，將會發生什麼樣的狀態
* Ans: 

```
pi@raspberrypi:/home $ echo 4 > /sys/class/gpio/export
pi@raspberrypi:/home $ echo out > /sys/class/gpio/gpio4/direction
pi@raspberrypi:/home $ echo 1 > /sys/class/gpio/gpio4/value
pi@raspberrypi:/home $ echo 0 > /sys/class/gpio/gpio4/value
pi@raspberrypi:/home $ echo 4 > /sys/class/gpio/unexport

# 卸載後繼續傳設定狀態資料，會出現錯誤如下
pi@raspberrypi:/home $ echo 1 > /sys/class/gpio/gpio4/value
-bash: /sys/class/gpio/gpio4/value: No such file or directory
pi@raspberrypi:/home $ 
```


## 作業2

* 使用 raspi-config 啟動 i2c，觀察 gpio2 以及 gpio3 的變化，透過 /sys/kernel/debug/gpio 觀察改變的情形，嘗試重新做一次作業1，針對 gpio2 以及 gpio3 操作，觀察在 i2c 啟動的狀態下，gpio2 以及 gpio3 相對 gpio4 有何不同
* Ans: 
	* 目前觀察啟動 i2c 與沒有啟動 i2c，沒有特別差異，詳細如下
	* gpio4

	```
	pi@raspberrypi:/home $ sudo cat /sys/kernel/debug/gpio
	gpiochip0: GPIOs 0-57, parent: platform/fe200000.gpio, pinctrl-bcm2711:
	 gpio-0   (ID_SDA              )
	 gpio-1   (ID_SCL              )
	 gpio-2   (SDA1                )
	 gpio-3   (SCL1                )
	 gpio-4   (GPIO_GCLK           )
	 gpio-5   (GPIO5               )
	 gpio-6   (GPIO6               )
	 gpio-7   (SPI_CE1_N           )
	 gpio-8   (SPI_CE0_N           )
	 gpio-9   (SPI_MISO            )
	 gpio-10  (SPI_MOSI            )
	 gpio-11  (SPI_SCLK            )
	 gpio-12  (GPIO12              )
	 gpio-13  (GPIO13              )
	 gpio-14  (TXD1                )
	 gpio-15  (RXD1                )
	 gpio-16  (GPIO16              )
	 gpio-17  (GPIO17              )
	 gpio-18  (GPIO18              )
	 gpio-19  (GPIO19              )
	 gpio-20  (GPIO20              )
	 gpio-21  (GPIO21              )
	 gpio-22  (GPIO22              )
	 gpio-23  (GPIO23              )
	 gpio-24  (GPIO24              )
	 gpio-25  (GPIO25              )
	 gpio-26  (GPIO26              )
	 gpio-27  (GPIO27              )
	 gpio-28  (RGMII_MDIO          )
	 gpio-29  (RGMIO_MDC           )
	 gpio-30  (CTS0                )
	 gpio-31  (RTS0                )
	 gpio-32  (TXD0                )
	 gpio-33  (RXD0                )
	 gpio-34  (SD1_CLK             )
	 gpio-35  (SD1_CMD             )
	 gpio-36  (SD1_DATA0           )
	 gpio-37  (SD1_DATA1           )
	 gpio-38  (SD1_DATA2           )
	 gpio-39  (SD1_DATA3           )
	 gpio-40  (PWM0_MISO           )
	 gpio-41  (PWM1_MOSI           )
	 gpio-42  (STATUS_LED_G_CLK    |led0                ) out lo 
	 gpio-43  (SPIFLASH_CE_N       )
	 gpio-44  (SDA0                )
	 gpio-45  (SCL0                )
	 gpio-46  (RGMII_RXCLK         )
	 gpio-47  (RGMII_RXCTL         )
	 gpio-48  (RGMII_RXD0          )
	 gpio-49  (RGMII_RXD1          )
	 gpio-50  (RGMII_RXD2          )
	 gpio-51  (RGMII_RXD3          )
	 gpio-52  (RGMII_TXCLK         )
	 gpio-53  (RGMII_TXCTL         )
	 gpio-54  (RGMII_TXD0          )
	 gpio-55  (RGMII_TXD1          )
	 gpio-56  (RGMII_TXD2          )
	 gpio-57  (RGMII_TXD3          )

	gpiochip1: GPIOs 504-511, parent: platform/soc:firmware:gpio, raspberrypi-exp-gpio, can sleep:
	 gpio-504 (BT_ON               )
	 gpio-505 (WL_ON               )
	 gpio-506 (PWR_LED_OFF         |led1                ) out lo ACTIVE LOW
	 gpio-507 (GLOBAL_RESET        )
	 gpio-508 (VDD_SD_IO_SEL       |vdd-sd-io           ) out hi 
	 gpio-509 (CAM_GPIO            )
	 gpio-510 (SD_PWR_ON           |sd_vcc_reg          ) out hi 
	 gpio-511 (SD_OC_N             )
	```

	* note: 啟動 gpio2 流程
		* `sudo raspi-config`，選擇 Interface Options，選擇 I2C，選擇 enabled
		* 重開機 `sudo reboot`
		* 把線改接到 gpio2
	* 啟動 gpio2

	```
	pi@raspberrypi:~ $ sudo cat /sys/kernel/debug/gpio
	gpiochip0: GPIOs 0-57, parent: platform/fe200000.gpio, pinctrl-bcm2711:
	 gpio-0   (ID_SDA              )
	 gpio-1   (ID_SCL              )
	 gpio-2   (SDA1                |sysfs               ) out hi 
	 gpio-3   (SCL1                )
	 gpio-4   (GPIO_GCLK           )
	 gpio-5   (GPIO5               )
	 gpio-6   (GPIO6               )
	 gpio-7   (SPI_CE1_N           )
	 gpio-8   (SPI_CE0_N           )
	 gpio-9   (SPI_MISO            )
	 gpio-10  (SPI_MOSI            )
	 gpio-11  (SPI_SCLK            )
	 gpio-12  (GPIO12              )
	 gpio-13  (GPIO13              )
	 gpio-14  (TXD1                )
	 gpio-15  (RXD1                )
	 gpio-16  (GPIO16              )
	 gpio-17  (GPIO17              )
	 gpio-18  (GPIO18              )
	 gpio-19  (GPIO19              )
	 gpio-20  (GPIO20              )
	 gpio-21  (GPIO21              )
	 gpio-22  (GPIO22              )
	 gpio-23  (GPIO23              )
	 gpio-24  (GPIO24              )
	 gpio-25  (GPIO25              )
	 gpio-26  (GPIO26              )
	 gpio-27  (GPIO27              )
	 gpio-28  (RGMII_MDIO          )
	 gpio-29  (RGMIO_MDC           )
	 gpio-30  (CTS0                )
	 gpio-31  (RTS0                )
	 gpio-32  (TXD0                )
	 gpio-33  (RXD0                )
	 gpio-34  (SD1_CLK             )
	 gpio-35  (SD1_CMD             )
	 gpio-36  (SD1_DATA0           )
	 gpio-37  (SD1_DATA1           )
	 gpio-38  (SD1_DATA2           )
	 gpio-39  (SD1_DATA3           )
	 gpio-40  (PWM0_MISO           )
	 gpio-41  (PWM1_MOSI           )
	 gpio-42  (STATUS_LED_G_CLK    |led0                ) out lo 
	 gpio-43  (SPIFLASH_CE_N       )
	 gpio-44  (SDA0                )
	 gpio-45  (SCL0                )
	 gpio-46  (RGMII_RXCLK         )
	 gpio-47  (RGMII_RXCTL         )
	 gpio-48  (RGMII_RXD0          )
	 gpio-49  (RGMII_RXD1          )
	 gpio-50  (RGMII_RXD2          )
	 gpio-51  (RGMII_RXD3          )
	 gpio-52  (RGMII_TXCLK         )
	 gpio-53  (RGMII_TXCTL         )
	 gpio-54  (RGMII_TXD0          )
	 gpio-55  (RGMII_TXD1          )
	 gpio-56  (RGMII_TXD2          )
	 gpio-57  (RGMII_TXD3          )

	gpiochip1: GPIOs 504-511, parent: platform/soc:firmware:gpio, raspberrypi-exp-gpio, can sleep:
	 gpio-504 (BT_ON               )
	 gpio-505 (WL_ON               )
	 gpio-506 (PWR_LED_OFF         |led1                ) out lo ACTIVE LOW
	 gpio-507 (GLOBAL_RESET        )
	 gpio-508 (VDD_SD_IO_SEL       |vdd-sd-io           ) out hi 
	 gpio-509 (CAM_GPIO            )
	 gpio-510 (SD_PWR_ON           |sd_vcc_reg          ) out hi 
	 gpio-511 (SD_OC_N             )
	```


## 作業3

* 使用 raspi-config 啟動 spi，觀察 gpio 各接腳的變化狀態，嘗試將 spi 關閉之後，透過 /sys/kernel/debug/gpio，觀察可以使用 gpio 數量的變化情形
* Ans: 
	* 啟動 spi 時，gpio7 與 gpio8 不一樣，詳細如下
	* 沒有啟動 spi

	```
	pi@raspberrypi:~ $ sudo cat /sys/kernel/debug/gpio
	gpiochip0: GPIOs 0-57, parent: platform/fe200000.gpio, pinctrl-bcm2711:
	 gpio-0   (ID_SDA              )
	 gpio-1   (ID_SCL              )
	 gpio-2   (SDA1                |sysfs               ) out hi 
	 gpio-3   (SCL1                )
	 gpio-4   (GPIO_GCLK           )
	 gpio-5   (GPIO5               )
	 gpio-6   (GPIO6               )
	 gpio-7   (SPI_CE1_N           )
	 gpio-8   (SPI_CE0_N           )
	 gpio-9   (SPI_MISO            )
	 gpio-10  (SPI_MOSI            )
	 gpio-11  (SPI_SCLK            )
	 gpio-12  (GPIO12              )
	 gpio-13  (GPIO13              )
	 gpio-14  (TXD1                )
	 gpio-15  (RXD1                )
	 gpio-16  (GPIO16              )
	 gpio-17  (GPIO17              )
	 gpio-18  (GPIO18              )
	 gpio-19  (GPIO19              )
	 gpio-20  (GPIO20              )
	 gpio-21  (GPIO21              )
	 gpio-22  (GPIO22              )
	 gpio-23  (GPIO23              )
	 gpio-24  (GPIO24              )
	 gpio-25  (GPIO25              )
	 gpio-26  (GPIO26              )
	 gpio-27  (GPIO27              )
	 gpio-28  (RGMII_MDIO          )
	 gpio-29  (RGMIO_MDC           )
	 gpio-30  (CTS0                )
	 gpio-31  (RTS0                )
	 gpio-32  (TXD0                )
	 gpio-33  (RXD0                )
	 gpio-34  (SD1_CLK             )
	 gpio-35  (SD1_CMD             )
	 gpio-36  (SD1_DATA0           )
	 gpio-37  (SD1_DATA1           )
	 gpio-38  (SD1_DATA2           )
	 gpio-39  (SD1_DATA3           )
	 gpio-40  (PWM0_MISO           )
	 gpio-41  (PWM1_MOSI           )
	 gpio-42  (STATUS_LED_G_CLK    |led0                ) out lo 
	 gpio-43  (SPIFLASH_CE_N       )
	 gpio-44  (SDA0                )
	 gpio-45  (SCL0                )
	 gpio-46  (RGMII_RXCLK         )
	 gpio-47  (RGMII_RXCTL         )
	 gpio-48  (RGMII_RXD0          )
	 gpio-49  (RGMII_RXD1          )
	 gpio-50  (RGMII_RXD2          )
	 gpio-51  (RGMII_RXD3          )
	 gpio-52  (RGMII_TXCLK         )
	 gpio-53  (RGMII_TXCTL         )
	 gpio-54  (RGMII_TXD0          )
	 gpio-55  (RGMII_TXD1          )
	 gpio-56  (RGMII_TXD2          )
	 gpio-57  (RGMII_TXD3          )

	gpiochip1: GPIOs 504-511, parent: platform/soc:firmware:gpio, raspberrypi-exp-gpio, can sleep:
	 gpio-504 (BT_ON               )
	 gpio-505 (WL_ON               )
	 gpio-506 (PWR_LED_OFF         |led1                ) out lo ACTIVE LOW
	 gpio-507 (GLOBAL_RESET        )
	 gpio-508 (VDD_SD_IO_SEL       |vdd-sd-io           ) out hi 
	 gpio-509 (CAM_GPIO            )
	 gpio-510 (SD_PWR_ON           |sd_vcc_reg          ) out hi 
	 gpio-511 (SD_OC_N 
	```
	
	* 啟動 spi

	```
	pi@raspberrypi:~ $ sudo cat /sys/kernel/debug/gpio
	gpiochip0: GPIOs 0-57, parent: platform/fe200000.gpio, pinctrl-bcm2711:
	 gpio-0   (ID_SDA              )
	 gpio-1   (ID_SCL              )
	 gpio-2   (SDA1                |sysfs               ) out hi 
	 gpio-3   (SCL1                )
	 gpio-4   (GPIO_GCLK           )
	 gpio-5   (GPIO5               )
	 gpio-6   (GPIO6               )
	 gpio-7   (SPI_CE1_N           |spi0 CS1            ) out hi ACTIVE LOW
	 gpio-8   (SPI_CE0_N           |spi0 CS0            ) out hi ACTIVE LOW
	 gpio-9   (SPI_MISO            )
	 gpio-10  (SPI_MOSI            )
	 gpio-11  (SPI_SCLK            )
	 gpio-12  (GPIO12              )
	 gpio-13  (GPIO13              )
	 gpio-14  (TXD1                )
	 gpio-15  (RXD1                )
	 gpio-16  (GPIO16              )
	 gpio-17  (GPIO17              )
	 gpio-18  (GPIO18              )
	 gpio-19  (GPIO19              )
	 gpio-20  (GPIO20              )
	 gpio-21  (GPIO21              )
	 gpio-22  (GPIO22              )
	 gpio-23  (GPIO23              )
	 gpio-24  (GPIO24              )
	 gpio-25  (GPIO25              )
	 gpio-26  (GPIO26              )
	 gpio-27  (GPIO27              )
	 gpio-28  (RGMII_MDIO          )
	 gpio-29  (RGMIO_MDC           )
	 gpio-30  (CTS0                )
	 gpio-31  (RTS0                )
	 gpio-32  (TXD0                )
	 gpio-33  (RXD0                )
	 gpio-34  (SD1_CLK             )
	 gpio-35  (SD1_CMD             )
	 gpio-36  (SD1_DATA0           )
	 gpio-37  (SD1_DATA1           )
	 gpio-38  (SD1_DATA2           )
	 gpio-39  (SD1_DATA3           )
	 gpio-40  (PWM0_MISO           )
	 gpio-41  (PWM1_MOSI           )
	 gpio-42  (STATUS_LED_G_CLK    |led0                ) out lo 
	 gpio-43  (SPIFLASH_CE_N       )
	 gpio-44  (SDA0                )
	 gpio-45  (SCL0                )
	 gpio-46  (RGMII_RXCLK         )
	 gpio-47  (RGMII_RXCTL         )
	 gpio-48  (RGMII_RXD0          )
	 gpio-49  (RGMII_RXD1          )
	 gpio-50  (RGMII_RXD2          )
	 gpio-51  (RGMII_RXD3          )
	 gpio-52  (RGMII_TXCLK         )
	 gpio-53  (RGMII_TXCTL         )
	 gpio-54  (RGMII_TXD0          )
	 gpio-55  (RGMII_TXD1          )
	 gpio-56  (RGMII_TXD2          )
	 gpio-57  (RGMII_TXD3          )

	gpiochip1: GPIOs 504-511, parent: platform/soc:firmware:gpio, raspberrypi-exp-gpio, can sleep:
	 gpio-504 (BT_ON               )
	 gpio-505 (WL_ON               )
	 gpio-506 (PWR_LED_OFF         |led1                ) out lo ACTIVE LOW
	 gpio-507 (GLOBAL_RESET        )
	 gpio-508 (VDD_SD_IO_SEL       |vdd-sd-io           ) out hi 
	 gpio-509 (CAM_GPIO            )
	 gpio-510 (SD_PWR_ON           |sd_vcc_reg          ) out hi 
	 gpio-511 (SD_OC_N             )
	```