# Graylog Content Pack for Watchguard

![graylog-cp-watchguard](https://user-images.githubusercontent.com/1869080/39520776-24204032-4e0c-11e8-8f13-65aae3a3fbc8.png)

This Content Pack enables you to parse the syslog logs which are generated and shipped by Watchguard Fireware. The Logs are parsed to enable dashboards, streams and structured search queries.  
The structure of the incoming logs depends on the kind of log which is marked with the message id defined by watchguard. To match all incoming logs there has to be an Extractor for each of those message ids.   
In addition to that this content pack adds Area, Name, Level and Description based on the message id. The information is added by using the lookup table(fireware_msg_id_lookup_table.csv).

[Overiew of Watchguard Message ID's](https://www.watchguard.com/help/docs/fireware/11/en-US/log_catalog/index.html)

#### Setup Watchguard to send log messages to graylog



![wg-logging1](https://user-images.githubusercontent.com/1869080/39520779-28f27486-4e0c-11e8-9b44-9fa86709bfba.PNG)

![wg-logging2](https://user-images.githubusercontent.com/1869080/39520783-2cb05bce-4e0c-11e8-9a53-792750355e26.PNG)


