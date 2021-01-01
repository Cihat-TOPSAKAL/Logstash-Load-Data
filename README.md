### Logstash Add Json log

 1. You need to change the content in the **logstash.conf** file;

        index => "your-index-name"

 2. For Csv file you need to change;

    * **docker-compose.yml**

            volumes:
            - ./logstash/logstash.yml:/usr/share/logstash/config/logstash.yml
            - ./logstash/logstash.conf:/usr/share/logstash/pipeline/logstash.conf
            - ./data/data.csv:/usr/share/logstash/external-data/data.csv

    * **logstash.conf**

            file {
                    start_position => "beginning"
                    path => "/usr/share/logstash/external-data/data.csv"
                    sincedb_path => "/dev/null" 
            }