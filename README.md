# Graylog Content Pack for Watchguard

![image](/Images/graylog-cp-watchguard.png)

This Content Pack enables you to parse the syslog logs which are generated and shipped by Watchguard Fireware. The Logs are parsed to enable dashboards, streams and structured search queries.  
The structure of the incoming logs depends on the kind of log which is marked with the message id defined by watchguard. To match all incoming logs there has to be an Extractor for each of those message ids.   
In addition to that this content pack adds Area, Name, Level and Description based on the message id. The information is added by using the lookup table(fireware_msg_id_lookup_table.csv).

[Overiew of Watchguard Message ID's](https://www.watchguard.com/help/docs/fireware/11/en-US/log_catalog/index.html)

#### Setup Watchguard to send log messages to graylog


![image](/wg-logging1.png)

![image](/Images/wg-logging1.png)

![image](/Images/wg-logging2.png)
