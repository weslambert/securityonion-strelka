# securityonion-strelka

![image](https://user-images.githubusercontent.com/16829864/51959540-ddc9f900-2422-11e9-9fbe-1ea1197c7d96.png)

#### Work in progress (not officially supported to work with Security Onion -- TEST AT YOUR OWN RISK!) 
  - Integrates the great work of [@jshlbrd](https://github.com/jshlbrd) ([Strelka](https://github.com/target/strelka)) with Security Onion. 
  - Tested on standalone and distributed Security Onion deployments.
  - **PLEASE NOTE**: [The official Strelka documentation](https://github.com/target/strelka#should-i-run-my-strelka-cluster-on-my-brosuricata-network-sensor) recommends that you install Strelka on a seperate node to perform processing of files without taxing sensor components.  These scripts will install Strelka directly on Security Onion (Standalone/Forward Node). Depending on the amount of traffic you are monitoring, and the number of files extracted by Bro (on average), you may indeed see the need to move Strelka (at least the server process) to a dedicated node (on the TODO list to have this as a future option).
  - Currently monitors `/nsm/strelka`.  Files are copied (every minute) from `/nsm/bro/extracted` to `/nsm/strelka`, then read by Strelka, and deleted after processed.  Original files remain in `/nsm/bro/extracted` and are managed by Security Onion as normal.  If you have a Security Onion installation with pre-existing extracted files (and you would like them scanned), you will need to manually copy these files to the `/nsm/strelka` directory.
  
#### TODO:
  - Better parsing/mapping of fields.
  - Better correlation with existing log data presented by Security Onion.
  - Consider moving/adding the ability to move Strelka server process to master server to avoid taxing sensor components.
  - Consider adding [Strelka Bro extraction script](https://github.com/target/strelka/blob/master/etc/bro/extract-strelka.bro).
  
##### Install on Standalone

- `wget https://raw.githubusercontent.com/weslambert/securityonion-strelka/grpc/install_strelka && sudo chmod +x install_strelka && sudo ./install_strelka`    

##### Install in Distributed Environment

Not currently supported.

##### Logs

- Raw logs are located in `/var/log/strelka/` (on standalone/forward nodes)

##### Kibana
- Navigate to `Discover` and type the following in the search field:
`tags:strelka` or `event_type:strelka`

    (May have to refresh field list under Management -> Index Patterns)
