# searchstax-client

#### Uploading Solr Config to Zookeepers

    ./zkcli.sh -zkhost ss111111-zk1.measuredsearch.com:2181,ss111111-zk2.measuredsearch.com:2181,ss111111-zk3.measuredsearch.com:2181 -cmd upconfig -confdir ../configsets/basic_configs/conf/ -confname test

#### Creating a collection

    curl 'https://ss111111-solr.measuredsearch.com/solr/admin/collections?action=CREATE&name=helloworld&collection.configName=test&numShards=3'
    
#### Uploading data to a collection

    curl  -X POST -H 'Content-type:application/json' -d @sample.json 'https://ss111111-solr.measuredsearch.com/solr/helloworld/update?commit=true'

#### Querying a collection

    curl 'https://ss111111-solr.measuredsearch.com/solr/helloworld/select?q=*:*&wt=json&indent=true'
    

