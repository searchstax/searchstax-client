# searchstax-client

#### Uploading Solr Config to Zookeepers

    ./zkcli.sh -zkhost ss111111-zk1.measuredsearch.com:2181,ss111111-zk2.measuredsearch.com:2181,ss111111-zk3.measuredsearch.com:2181 -cmd upconfig -confdir ../configsets/basic_configs/conf/ -confname test

#### Creating a collection

    curl 'https://ss1111-solr.measuredsearch.com/solr/admin/collections?action=CREATE&name=helloworld&collection.configName=test&numShards=3'
    
#### Querying a collection

    curl 'https://ss1111-solr.measuredsearch.com/solr/helloworld/select?q=*:*&wt=json&indent=true'
