# 作業

## 作業1

* 練習使用一個民生物聯網 API，例如空氣、地震等感測站所回傳的紀錄資料。
* 參考資料網址： https://ci.taiwan.gov.tw/dsp/environmental.aspx
* Ans: 
	* 環保署 - 智慧城鄉空品微型感測器 <https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things?$expand=Locations&$select=name,properties&$count=true>
	* 取得 id 為 1 的資料 <https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(1)?$expand=Locations&$select=name,properties&$count=true> 

	```json
	{
	   "name":"智慧城鄉空品微型感測器-11113765144",
	   "properties":{
	      "city":"基隆市",
	      "areaType":"一般社區",
	      "isMobile":"false",
	      "township":"七堵區",
	      "authority":"行政院環境保護署",
	      "isDisplay":"true",
	      "isOutdoor":"true",
	      "stationID":"11113765144",
	      "locationId":"TW020201D0506810",
	      "Description":"廣域SAQ-210",
	      "areaDescription":"七堵區"
	   },
	   "Locations@iot.count":1,
	   "Locations":[
	      {
	         "description":"智慧城鄉空品微型感測器-11113765144",
	         "encodingType":"application/vnd.geo+json",
	         "@iot.id":1,
	         "location":{
	            "type":"Point",
	            "coordinates":[
	               121.687045,
	               25.111078
	            ]
	         },
	         "name":"智慧城鄉空品微型感測器-11113765144",
	         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Locations(1)"
	      }
	   ]
	}
	```


## 作業2

* 練習操作 OGC SensorThings API，將環保局測站位置的資料抓取下來，並且觀察下載資料的內容。
* 參考網址：https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things
* Ans: 
	* value 有多組，省略後面比數

	```json
	{
	   "@iot.count":9703,
	   "@iot.nextLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things?$skip=100",
	   "value":[
	      {
	         "description":"智慧城鄉空品微型感測器-11113765144",
	         "@iot.id":1,
	         "name":"智慧城鄉空品微型感測器-11113765144",
	         "properties":{
	            "city":"基隆市",
	            "areaType":"一般社區",
	            "isMobile":"false",
	            "township":"七堵區",
	            "authority":"行政院環境保護署",
	            "isDisplay":"true",
	            "isOutdoor":"true",
	            "stationID":"11113765144",
	            "locationId":"TW020201D0506810",
	            "Description":"廣域SAQ-210",
	            "areaDescription":"七堵區"
	         },
	         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(1)",
	         "Locations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(1)/Locations",
	         "HistoricalLocations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(1)/HistoricalLocations",
	         "TaskingCapabilities@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(1)/TaskingCapabilities",
	         "Datastreams@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(1)/Datastreams",
	         "MultiDatastreams@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(1)/MultiDatastreams"
	      },
	      {
	         "description":"智慧城鄉空品微型感測器-11183695772",
	         "@iot.id":2,
	         "name":"智慧城鄉空品微型感測器-11183695772",
	         "properties":{
	            "city":"台中市",
	            "areaType":"社區",
	            "isMobile":"false",
	            "township":"大雅區",
	            "authority":"行政院環境保護署",
	            "isDisplay":"true",
	            "isOutdoor":"true",
	            "stationID":"11183695772",
	            "locationId":"TW090208A0507633",
	            "Description":"廣域SAQ-210",
	            "areaDescription":"大雅區"
	         },
	         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(2)",
	         "Locations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(2)/Locations",
	         "HistoricalLocations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(2)/HistoricalLocations",
	         "TaskingCapabilities@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(2)/TaskingCapabilities",
	         "Datastreams@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(2)/Datastreams",
	         "MultiDatastreams@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(2)/MultiDatastreams"
	      },
	      {
	         "description":"智慧城鄉空品微型感測器-9330689794",
	         "@iot.id":3,
	         "name":"智慧城鄉空品微型感測器-9330689794",
	         "properties":{
	            "city":"苗栗縣",
	            "areaType":"工業區",
	            "isMobile":"false",
	            "township":"苗栗市",
	            "authority":"行政院環境保護署",
	            "isDisplay":"true",
	            "isOutdoor":"true",
	            "stationID":"9330689794",
	            "locationId":"A0191",
	            "Description":"經昌/CE003",
	            "areaDescription":"西山工業區"
	         },
	         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(3)",
	         "Locations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(3)/Locations",
	         "HistoricalLocations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(3)/HistoricalLocations",
	         "TaskingCapabilities@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(3)/TaskingCapabilities",
	         "Datastreams@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(3)/Datastreams",
	         "MultiDatastreams@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Things(3)/MultiDatastreams"
	      }
	   ]
	}
	```


## 作業3 : 
* 依據作業 2 所下載的各個環保局測站感測器的描述資料，進一步點選 Datastreams、Locations，以及 Datastreams 點選進入後，點選 Observations 的 URL，觀察所下載到的資料內容，其中 Observations 內部是否包含個別感測器紀錄的資料。
* Ans: 
	* 點選第一筆的 `Datastreams@iot.navigationLink`

	```json
	{
	   "@iot.count":3,
	   "value":[
	      {
	         "description":"細懸浮微粒 PM2.5",
	         "@iot.id":1,
	         "name":"PM2.5",
	         "observationType":"http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement",
	         "observedArea":{
	            "type":"Point",
	            "coordinates":[
	               121.687045,
	               25.111078
	            ]
	         },
	         "phenomenonTime":"2021-03-20T09:01:28.000Z/2021-03-20T13:47:28.000Z",
	         "resultTime":null,
	         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)",
	         "unitOfMeasurement":{
	            "name":"microgram per cubic meter",
	            "symbol":"μg/m3",
	            "definition":"https://acronyms.thefreedictionary.com/ug%2Fm3"
	         },
	         "ObservedProperty@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)/ObservedProperty",
	         "Sensor@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)/Sensor",
	         "Thing@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)/Thing",
	         "Observations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)/Observations"
	      },
	      {
	         "description":"溫度",
	         "@iot.id":3,
	         "name":"Temperature",
	         "observationType":"http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement",
	         "observedArea":{
	            "type":"Point",
	            "coordinates":[
	               121.687045,
	               25.111078
	            ]
	         },
	         "phenomenonTime":"2021-03-20T09:01:28.000Z/2021-03-20T13:47:28.000Z",
	         "resultTime":null,
	         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)",
	         "unitOfMeasurement":{
	            "name":"degree celsius",
	            "symbol":"°C",
	            "definition":"https://en.wikipedia.org/wiki/Celsius"
	         },
	         "ObservedProperty@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)/ObservedProperty",
	         "Sensor@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)/Sensor",
	         "Thing@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)/Thing",
	         "Observations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(3)/Observations"
	      },
	      {
	         "description":"相對溼度",
	         "@iot.id":2,
	         "name":"Relative humidity",
	         "observationType":"http://www.opengis.net/def/observationType/OGC-OM/2.0/OM_Measurement",
	         "observedArea":{
	            "type":"Point",
	            "coordinates":[
	               121.687045,
	               25.111078
	            ]
	         },
	         "phenomenonTime":"2021-03-20T09:01:28.000Z/2021-03-20T13:47:28.000Z",
	         "resultTime":null,
	         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)",
	         "unitOfMeasurement":{
	            "name":"percentage",
	            "symbol":"%",
	            "definition":"https://en.wikipedia.org/wiki/Percentage"
	         },
	         "ObservedProperty@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)/ObservedProperty",
	         "Sensor@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)/Sensor",
	         "Thing@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)/Thing",
	         "Observations@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(2)/Observations"
	      }
	   ]
	}
	```

	* 點選第一筆的 `Observations@iot.navigationLink`，value 有多筆省略，包含個別感測器紀錄的資料

	```json
	{
	   "@iot.count":172,
	   "@iot.nextLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Datastreams(1)/Observations?$skip=100",
	   "value":[
	      {
	         "@iot.id":1430206809,
	         "phenomenonTime":"2021-03-20T13:07:28.000Z",
	         "result":11.92,
	         "resultTime":null,
	         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Observations(1430206809)",
	         "MultiDatastream@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Observations(1430206809)/MultiDatastream",
	         "FeatureOfInterest@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Observations(1430206809)/FeatureOfInterest",
	         "Datastream@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Observations(1430206809)/Datastream"
	      },
	      {
	         "@iot.id":1430154068,
	         "phenomenonTime":"2021-03-20T13:03:29.000Z",
	         "result":11.08,
	         "resultTime":null,
	         "@iot.selfLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Observations(1430154068)",
	         "MultiDatastream@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Observations(1430154068)/MultiDatastream",
	         "FeatureOfInterest@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Observations(1430154068)/FeatureOfInterest",
	         "Datastream@iot.navigationLink":"https://sta.ci.taiwan.gov.tw/STA_AirQuality_EPAIoT/v1.0/Observations(1430154068)/Datastream"
	      }
	   ]
	}
	```