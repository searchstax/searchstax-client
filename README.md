# searchstax-client

#### Uploading Solr Config to Zookeepers

    ./zkcli.sh -zkhost ss111111-zk1.measuredsearch.com:2181,ss111111-zk2.measuredsearch.com:2181,ss111111-zk3.measuredsearch.com:2181 -cmd upconfig -confdir ../configsets/basic_configs/conf/ -confname test
