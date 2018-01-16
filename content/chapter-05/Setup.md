# Setup #

1. Logstash requires Java 8 Oracle or OpenJDK, Java 9 is not supported
2. Linux distribution repository is available similary to other Elastic.co products
3. A [Docker image](https://www.elastic.co/guide/en/logstash/current/docker.html) has been made available by Elastic.co, more about docker later...
4. If installing manually - do not install into a directory path that contains colon (:) characters
5. Pipeline configuration files define the Logstash processing pipeline: ALL files in /etc/logstash/conf.d folder
NOTE: Logstash 6.0 and higher has support for running multiple pipelines which defined in pipelines.yml file.
6. Settings files specify options for Logstash startup and execution:
    6.1 /etc/logstash/logstash.yml - configuration flags
    6.2 /etc/logstash/startup.options - used by system-install to create logstash service or services
7. Basic pipeline with Logstash
![Basic Pipeline](../../media/basic_logstash_pipeline.png)
