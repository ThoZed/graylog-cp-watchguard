# Graylog Content Pack for Watchguard


![graylog-cp-watchguard](https://user-images.githubusercontent.com/1869080/39520776-24204032-4e0c-11e8-8f13-65aae3a3fbc8.png)

This Content Pack enables you to parse the logs which are generated and shipped by Watchguard Fireware. The Logs are parsed to enable dashboards, streams and structured search queries.  

###  Fireware log format

The logs messages include a message ID which could be extracted by using following Expression.

`^.*msg_id=\"(\S\S\S\S-\S\S\S\S)\"`

The resulting msg_id is used by the extractors to lookup msg_name,msg_area,msg_level and msg_desc fields.

With the help od this information it is more easy to read the incoming log messages. Every message provides additional information which could be used for search queries.

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

1. content_pack_lookuptables.json
2. content_pack_input.json

please apply the lookuptables first.

*if you run into trouble while importing or updating it may be helpful to remove every component an start fresh.*

### Extractors

### Dashboards
