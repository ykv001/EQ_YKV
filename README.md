# EQ_YKV
Work Sample Problems - Data Role

 file: *EQ_ykv.py*
 
 output visible on: *EQ_ykv_output.ipynb*

#### 0 Cleanup

Data with same time stamp and location information was removed (2026 requests). Request outside Canada, wrongly labeled were removed as well. Over 90 % of the sample data was usable. 1 POI was discarded for having repeated location.

#### 1 Label

3 POIs were assigned to the curated data, distance units are in kilometers. 

Cleaned records: 19871
 
 
          +-------+--------------------+---------+---------------+------------------+
          |    _ID|              TimeSt|     City|            POI|           minDist|
          +-------+--------------------+---------+---------------+------------------+
          |4523251|2017-06-21 19:00:...|   Guelph|POI2 - MONTREAL| 583.1789340044905|
          |4530411|2017-06-21 04:00:...|Thornhill|POI2 - MONTREAL| 502.5864355114627|
          |4544563|2017-06-21 15:01:...|  Toronto|POI2 - MONTREAL|501.54997848296216|
          |4550906|2017-06-21 05:01:...|   London|POI2 - MONTREAL| 683.3587874652333|
          |4573277|2017-06-21 09:01:...|  Renfrew|POI2 - MONTREAL| 243.2407245730464|
          |4575633|2017-06-21 13:02:...|Vancouver|POI1 - EDMONTON| 845.8776323682429|
          |4582656|2017-06-21 17:02:...|  Calgary|POI1 - EDMONTON|281.78694962282947|
          |4584527|2017-06-21 15:02:...|    Laval|POI2 - MONTREAL| 19.74598382920213|
          |4584920|2017-06-21 10:02:...| Wrentham|POI1 - EDMONTON|464.78356080913017|
          |4585618|2017-06-21 05:02:...|  Calgary|POI1 - EDMONTON|293.85650299885936|
          |4586259|2017-06-21 08:02:...|  Lacombe|POI1 - EDMONTON|121.32335536718419|
          |4602217|2017-06-21 09:04:...|  Toronto|POI2 - MONTREAL| 510.8201388633522|
          |4614987|2017-06-21 08:05:...|   Milton|POI2 - MONTREAL| 555.9820409522475|
          |4637235|2017-06-21 16:06:...|Newmarket|POI2 - MONTREAL|500.00799128225253|
          |4637946|2017-06-21 03:06:...|   Ottawa|POI2 - MONTREAL|171.12503931738408|
          |4663453|2017-06-21 16:08:...| Red Deer|POI1 - EDMONTON|146.80490191256672|
          |4664983|2017-06-21 16:08:...|   Oshawa|POI2 - MONTREAL|460.99006328050314|
          |4691479|2017-06-21 00:10:...|  Calgary|POI1 - EDMONTON|  285.196423291003|
          |4697224|2017-06-21 19:11:...|  Calgary|POI1 - EDMONTON| 279.9691099779517|
          |4703272|2017-06-21 15:11:...| Montréal|POI2 - MONTREAL|1.3899278655994876|
          +-------+--------------------+---------+---------------+------------------+

#### 2 Analysis

Summary statistis revealed that the requests assigned to each poi are very close to be normaly distributed: similar mean and median, skewsness close to zero and kutosis less than 3 units. The value of the POI radius calculated includes all the requests in that POI. 

          +------------------+------------------+
          |               POI|      avg(minDist)|
          +------------------+------------------+
          |   POI2 - MONTREAL|458.34837448221276|
          |   POI1 - EDMONTON|294.85557983841613|
          |POI3 - NOVA SCOTIA|146.49472942297874|
          +------------------+------------------+

          +------------------+--------------------+
          |               POI|stddev_samp(minDist)|
          +------------------+--------------------+
          |   POI2 - MONTREAL|    228.108239364406|
          |   POI1 - EDMONTON|   287.6127766447783|
          |POI3 - NOVA SCOTIA|   79.89855056387565|
          +------------------+--------------------+

          +------------------+-------------------+
          |               POI|       min(minDist)|
          +------------------+-------------------+
          |   POI2 - MONTREAL| 0.8093687171976599|
          |   POI1 - EDMONTON|0.34844834633502614|
          |POI3 - NOVA SCOTIA| 16.227691135268355|
          +------------------+-------------------+

          +------------------+------------------+
          |               POI|      max(minDist)|
          +------------------+------------------+
          |   POI2 - MONTREAL|1497.6822580304956|
          |   POI1 - EDMONTON|1483.0054158570954|
          |POI3 - NOVA SCOTIA| 558.6544170261211|
          +------------------+------------------+

          +------------------+-------------------+
          |               POI|  skewness(minDist)|
          +------------------+-------------------+
          |   POI2 - MONTREAL|0.06694264070652206|
          |   POI1 - EDMONTON| 1.4241489936386473|
          |POI3 - NOVA SCOTIA| 0.9532915462390601|
          +------------------+-------------------+

          +------------------+------------------+
          |               POI| kurtosis(minDist)|
          +------------------+------------------+
          |   POI2 - MONTREAL| 2.331133468737165|
          |   POI1 - EDMONTON|2.0224187402527862|
          |POI3 - NOVA SCOTIA|1.9436436818666118|
          +------------------+------------------+


       +--------+------------------+------------------+------------------+------------------+-----------------------+
       |Requests|               POI|              Mean|            Median|      poiRadius_km|Density_Requests_by_km2|
       +--------+------------------+------------------+------------------+------------------+-----------------------+
       |    9816|   POI2 - MONTREAL|458.34837448221276|511.67044847139715|1497.6822580304956|   0.001392982542784...|
       |    9695|   POI1 - EDMONTON|294.85557983841613|277.56092637638926|1483.0054158570954|   0.001403178215004784|
       |     360|POI3 - NOVA SCOTIA|146.49472942297874| 152.5009259557654| 558.6544170261211|   3.671694349361896E-4|
       +--------+------------------+------------------+------------------+------------------+-----------------------+

