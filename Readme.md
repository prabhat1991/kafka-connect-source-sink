Kafka Connect Distributed Mode in windows using kafka-binaries
----------------------------------------------------------------

==========FileStream Source============

1. Set-Up the kafka cluster local
2. Start zookeeper and different configured brokers
3. $Kafka_Home/config/connect-distributed.properties is responsible for configuring the kafka connect in distributed mode. Please refer the attached configuration file.
4. Start the kafka connect in distributed mode bin\windows\connect-distributed.bat config\connect-distributed.properties.
5. kafka-connect UI is accessible at http://localhost:8083 port 8083 being the default.
6. To configure the source configuration we need to provide the configuration json as a POST to kafka-connect api at http://localhost:8083/connectors. Reference kafka-connect-source-config.json
7. Place the file at the root directory or drive where the kafka cluster is running from.
8. For each line saved in the file the console-consumer would pick the entries from kafka sent to cluster via the File Stream Source connector


=============Twitter Source==============

This Twitter Source connector is used to pull data from Twitter in realtime.

name=connector1
tasks.max=1
connector.class=com.github.jcustenborder.kafka.connect.twitter.TwitterSourceConnector

# Set these required values
twitter.oauth.accessTokenSecret=
process.deletes=
filter.keywords=
kafka.status.topic=
kafka.delete.topic=
twitter.oauth.consumerSecret=
twitter.oauth.accessToken=
twitter.oauth.consumerKey=


| Name                            | Description                                       | Type     | Default | Valid Values | Importance |
|---------------------------------|---------------------------------------------------|----------|---------|--------------|------------|
| filter.keywords                 | Twitter keywords to filter for.                   | list     |         |              | high       |
| filter.userIds                  | Twitter user IDs to follow.                       | list     | ""      |              | low        |
| kafka.delete.topic              | Kafka topic to write delete events to.            | string   |         |              | high       |
| kafka.status.topic              | Kafka topic to write the statuses to.             | string   |         |              | high       |
| process.deletes                 | Should this connector process deletes.            | boolean  |         |              | high       |
| twitter.oauth.accessToken       | OAuth access token                                | password |         |              | high       |
| twitter.oauth.accessTokenSecret | OAuth access token secret                         | password |         |              | high       |
| twitter.oauth.consumerKey       | OAuth consumer key                                | password |         |              | high       |
| twitter.oauth.consumerSecret    | OAuth consumer secret                             | password |         |              | high       |
| twitter.debug                   | Flag to enable debug logging for the twitter api. | boolean  | false   |              | low        |

===========Elastic Search=========== 
