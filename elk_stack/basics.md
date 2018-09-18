#### What is a log?
--> representation of an event in a **human readable** and **machine parseable** format
*LOG = TIMESTAMP + DATA*

Tips for successful loggin:
* DO NOT INVENT A TIME FORMAT, use the ISO 8601
* strict formatting, plaintext and no weird unicode characters
* do not log passwords
* use different levels of logging(WARN,DEBUG,INFO)


##### Logstash
* aggregates the data from different places
* offers a lot of options to filter and output the data

##### Elastic search
* distributed system used to index the data
* real time search and analytics engine
* *the recommended output for **logstash***
* RESTful API













---
- [ ] [More on logging](https://theagileadmin.com/2010/08/20/logging-for-success/)