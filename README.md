# securityonion-strelka
#### Work in progress 
  - Tested on standalone install of Security Onion, but *should* work using forward nodes, with filebeat.yml pointed to master server.         Currently monitors `/nsm/bro/extracted`.

- Install Strelka   
`git clone https://github.com/target/strelka.git /opt/strelka/`    
`cd /opt/strelka/ && docker build -t so-strelka .`

- Download Security Onion stuff    
`cd ~ &&  git clone https://github.com/weslambert/securityonion-strelka.git`    

- Make dirs and set perms    
`mkdir -p /var/log/strelka/ /etc/strelka`    
`chown -R 1001:1001 /var/log/strelka /etc/strelka`    

- Strelka config files    
`cp securityonion-strelka/etc/dirstream.yml /etc/strelka`    

- Copy Strelka Docker start/stop/restart/files    
`cp securityonion-strelka/usr/sbin/so-* /usr/sbin/`        

- Install Filebeat   
`curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-6.4.2-amd64.deb`    
`dpkg -i filebeat-6.4.2-amd64.deb`    

- Copy filebeat.yml and modify to point to Logstash instance    
`cp securityonion-strelka/etc/filebeat/filebeat.yml /etc/filebeat/`           

- Start Filebeat and enable at boot    
`service filebeat start`        
`systemctl enable filebeat.service`        

- If storage node or standalone, copy Logtash config files    
`cp securityonion-strelka/etc/logstash/* /etc/logstash/custom/`    
`so-logstash-restart`   

- Run Strelka   
`so-strelka-start` 
