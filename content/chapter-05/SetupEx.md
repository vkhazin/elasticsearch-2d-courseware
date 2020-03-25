# Setup Excercise

1. Download and install the Public Signing Key, not required as we have added it previously:  
   ```
   wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
   ```
2. Add repository definition, not required as we have added it previously:  
   ```
   echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | \
       sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list &&
   sudo apt-get update
   ```
3. Install logstash from the repository:  
   ```
   sudo apt-get install logstash
   ```
4. Create a manual pipeline for Logstash
   ```
    cd /usr/share/logstash
    sudo bin/logstash -e 'input { stdin { } } output { stdout {} }'
   ```
5. `-e` enables specifying configuration directly from the command line
6. stdin: filehandle that process reads to get information from you, human
7. stdout: process writes log information to this filehandle
8. After the pipeline has started  
   ```
   ...Pipelines running...
   ```

   type in the terminal:
   ```
   Hello World!
   ```

   And press enter
9. Expected response:
   ```
   {
     "host" => "ip-172-31-19-36",
     "message" => "Hello World!",
     "@timestamp" => 2020-03-25T23:00:16.476Z,
     "@version" => "1"
   }
   ```
10. Logstash adds a timestamp, version and the hostname to the message we sent
11. To exit Logstash use keyboard combination ctrl-d and it will shut down the process



