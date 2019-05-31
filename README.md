![graylog-cp-watchguard_2](https://user-images.githubusercontent.com/1869080/43983109-2e9316ca-9cf9-11e8-86e8-2f7a818f03dd.png)


# Graylog Content Pack for Watchguard

This Content Pack enables you to parse the logs which are generated and shipped by Watchguard Fireware. The Logs are parsed to enable dashboards, streams and structured search queries.  

###  Fireware log format

The logs messages include a message ID which could be extracted by using following Expression.

`^.*msg_id=\"(\S\S\S\S-\S\S\S\S)\"`

The resulting msg_id is used by the extractors to lookup msg_name,msg_area,msg_level and msg_desc fields.

With the help of this information it is more easy to read the incoming log messages. Every message provides additional information which could be used for search queries.

The extractor calls a lookup table which uses a data adapter to read the [csv](LookupTables/fireware_msg_id_lookup_table.csv) file.

This file is a list similar to the [Fireware log catalog](https://www.watchguard.com/help/docs/fireware/11/en-US/log_catalog/index.html)

### Prerequisites

1. graylog up and running :)
    - [Installing Graylog](http://docs.graylog.org/en/latest/pages/installation.html#installing-graylog)
2. copy [csv](LookupTables/) files to `/etc/graylog`
3. configure Fireware to send logs

    System Manager -> Setup -> Logging -> - [x] send syslog mess...

   -IP-Address: <graylog host>

   -Port: 55514


### Import Content Pack

Because you have to import the content in order the content pack consists following files:

1. content_pack_1_DataAdapter.json
2. content_pack_2_LookupTables.json
3. content_pack_3_Input.json
4. content_pack_4_Dashboard.json

please always apply in this order.

*if you run into trouble while importing or updating it may be helpful to remove every component an start fresh.*

### Streams

With the help of streams it is possible to narrow your search results to following areas:

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

The Streams are also useful to allow user access only for certain messages.

### Dashboard

With the **_integrator panel_** you are able to see which messages have a missing extractor. The timeline shows incoming and unextracted messages.

<img src="https://user-images.githubusercontent.com/1869080/41641816-ccbeb338-7466-11e8-9243-bedfc2f2542e.PNG" width="600">

With the **_incident panel_** you have a quick oulook about firewall traffic and see counts of the different messages types.
Its also a good point to start digging the logs, in case of an incident.

<img src="https://user-images.githubusercontent.com/1869080/42139130-4ab43fa4-7d88-11e8-94dd-c03955f58594.PNG" width="600">

### Contribute

Please help adding Extractors to the input to be able to do a structured search on every kind of msg_id.

How to:

- find missing extractor for msg_id
- figure out on which way values could be matched
- build regex,grok, ...
- test 
- create pull request

Thanks:-)

Example:






