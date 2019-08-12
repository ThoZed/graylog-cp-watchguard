![graylog-cp-watchguard_2](https://user-images.githubusercontent.com/1869080/62893417-d9c05180-bd4a-11e9-8970-90081c1e5368.png)


# Graylog Content Pack for Watchguard

This content pack sturctures and enriches log messages which are generated and shipped by Watchguard Fireware. The logs are parsed to enable all the wonderful features of Graylog. :-) 

###  Fireware log format

The log messages include a message ID which can be extracted by the following expression.

`^.*msg_id=\"(\S\S\S\S-\S\S\S\S)\"`

The resulting msg_id is used by the extractors to lookup msg_name,msg_area,msg_level and msg_desc fields.

With the help of this information it is easier to read the incoming log messages. Every message provides additional information which can be used for search queries.

The extractor access a lookup table which uses a data adapter to read the [csv](LookupTables/fireware_msg_id_lookup_table.csv) file.

This file is a list similar to the [Fireware log catalog](https://www.watchguard.com/help/docs/fireware/11/en-US/log_catalog/index.html)

The msg_id is used as a key to identify the format of the log message. Based on that the extractor rule of the graylog input is setup for each msg_id separately. 

### Prerequisites

1. graylog up and running :)
    - [Installing Graylog](http://docs.graylog.org/en/latest/pages/installation.html#installing-graylog)
2. copy [csv](LookupTables/) files to `/etc/graylog`
3. configure Fireware to send logs

    System Manager -> Setup -> Logging -> - [x] send syslog mess...

   -IP-Address: <graylog host>

   -Port: 55514(content pack default port)


### Import Content Pack

You can import the complete content in one File. Just upload [content-pack-graylog-cp-watchguard.json](content-pack-graylog-cp-watchguard.json) in System/Content Pack Section of Graylog and install.
With the parameters for input port and lookup table file path you can customize the content pack to suit your needs. 

*if you run into trouble while importing or updating it may be helpful to remove every component an start afresh.*

### Streams

With the help of streams it is possible to narrow your search results to the following areas:

- Proxy
- Management
- Firewall
- Networking
- Cluster
- Security Services
- VPN
- Mobile Security
- INFO
- WARNING
- ERROR
- DEBUG

The streams are also useful to allow user access only for certain messages.

### Dashboard

With the **_integrator panel_** you are able to see which messages have a missing extractor. The timeline shows incoming and unextracted messages.

<img src="https://user-images.githubusercontent.com/1869080/41641816-ccbeb338-7466-11e8-9243-bedfc2f2542e.PNG" width="600">

With the **_incident panel_** you have a quick overview of firewall traffic and counts of different messages types.
Its also a good point to start digging the logs, in case of an incident. The fact that graylog also provides an alert engine as well as an plugin for thread intelligence you can turn your Watchguard into an universal adaptable SIEM enabled device.


<img src="https://user-images.githubusercontent.com/1869080/42139130-4ab43fa4-7d88-11e8-94dd-c03955f58594.PNG" width="600">

### Contribute

Please help adding extractors to the input to be able to facilitate structured searches of every kind of msg_id.

How to:

- find missing extractor for msg_id
- figure out how values can be matched
- build regex,grok, ... 
    use: https://grokconstructor.appspot.com/do/match
    or: https://www.debuggex.com/
- test 
- create pull request

cheers:-)






