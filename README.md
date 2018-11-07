# securityonion-strelka
#### Work in progress (not officially supported to work with Security Onion -- TEST AT YOUR OWN RISK!) 
  - Integrates the great work of [@jshlbrd](https://github.com/jshlbrd) ([Strelka](https://github.com/target/strelka)) with Security Onion 
  - Tested on standalone and distributed Security Onion deployments.         
  - Currently monitors `/nsm/bro/extracted`.
  
##### Install on Standalone

- `wget https://raw.githubusercontent.com/weslambert/securityonion-strelka/master/install_strelka && sudo chmod +x install_strelka && sudo ./install_strelka`    

##### Install in Distributed Environment

From the master:

- `wget https://raw.githubusercontent.com/weslambert/securityonion-strelka/master/install_strelka_master && sudo chmod +x install_strelka_master && sudo ./install_strelka_master`    

##### Logs

- Raw logs are located in `/var/log/strelka/` (on standalone/forward nodes)

##### Kibana
- Navigate to `Discover` and type the following in the search field:
`tags:strelka` or `event_type:strelka`

    (May have to refresh field list under Management -> Index Patterns)
