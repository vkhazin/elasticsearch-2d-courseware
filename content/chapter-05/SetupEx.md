# Setup Excercise #

1. Download and install the Public Signing Key:  
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```
2. Add repository definition:  
```
sudo apt-get install apt-transport-https
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
```
3. Install logstash from repository:  
```
sudo apt-get update && sudo apt-get install logstash
```
4. Create a manual pipeline for Logstash
    ```
    cd /usr/share/logstash
    sudo bin/logstash -e 'input { stdin { } } output { stdout {} }'
    ```
5. -e: enable specifying configuration directly from the command line
6. stdin: file handle that process reads to get information from you, human
7. stdout: process writes log information to this file handle
8. After pipeline has started  
  ```
  The stdin plugin is now waiting for input:
  ```
  type in the terminal:
  ```
  Hello World!
  ```
And press enter
9. Expected response:
```
  {
    "@version" => "1",
    "host" => "ip-172-31-16-19",
    "@timestamp" => 2018-06-12T06:47:55.703Z,
    "message" => "Hello World!"
  }
```
10. Logstash adds a timestamp and hostname to the message we sent
11. To exit Logstash use keyboard combination ctrl-d
