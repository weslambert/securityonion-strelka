# securityonion-strelka
#### Work in progress 
  - Tested on standalone install of Security Onion, but *should* work using forward nodes, with filebeat.yml pointed to master server.         Currently monitors `/nsm/bro/extracted`.

- `wget https://raw.githubusercontent.com/weslambert/securityonion-strelka/master/install_strelka && sudo chmod +x install_strelka && sudo ./install_strelka`    

View the logs:

In Kibana, navigate to `Discover` and type the following in the search field:
`tags:strelka` or `event_type:strelka`

(May have to refresh field list under Management -> Index Patterns)
