# Searchstax Client

## For versions 6.6.2 and below

* Uploading Solr Config to Zookeepers
```
./zkcli.sh -zkhost ss111111-zk1.measuredsearch.com:2181,ss111111-zk2.measuredsearch.com:2181,ss111111-zk3.measuredsearch.com:2181 -cmd upconfig -confdir ../configsets/basic_configs/conf/ -confname test
```

* Creating a collection
```
curl 'https://ss111111-solr.measuredsearch.com/solr/admin/collections?action=CREATE&name=helloworld&collection.configName=test&numShards=3'
```

* Uploading data to a collection
```
curl  -X POST -H 'Content-type:application/json' -d @sample.json 'https://ss111111-solr.measuredsearch.com/solr/helloworld/update?commit=true'
```

* Querying a collection
```
curl 'https://ss111111-solr.measuredsearch.com/solr/helloworld/select?q=*:*&wt=json&indent=true'
```    

## For versions 7.1.1 and above

* __Uploading a solr config to zookeeper__
```
./zkcli.sh -zkhost ss108280-1-us-east-1-aws.searchstax.co:2181 -cmd upconfig -confdir ../configsets/_default/conf/ -confname rahultestconfig 
```

* __Creating a collection__
```
curl 'https://ss108280-1-us-east-1-aws.searchstax.co/solr/admin/collections?action=CREATE&name=hellorahul&collection.configName=rahultestconfig&numShards=1&replicationFactor=1&maxShardsPerNode=1' -k
```
On success, it will produce an o/p
```
{
  "responseHeader":{
    "status":0,
    "QTime":3132},
  "success":{
    "10.0.0.182:8983_solr":{
      "responseHeader":{
        "status":0,
        "QTime":1889},
      "core":"hellorahul_shard1_replica_n1"}}}
```

* __Uploading data to a collection__
```
curl -X POST -H 'Content-type:application/json' -d @sample.json 'https://ss108280-1-us-east-1-aws.searchstax.co/solr/hellorahul/update?commit=true' -k
```
On success, it will produce an o/p
```
{
  "responseHeader":{
    "status":0,
    "QTime":47}}
```

* __Querying a collection__
```
curl 'https://ss108280-1-us-east-1-aws.searchstax.co/solr/hellorahul/select?q=*:*&wt=json&indent=true' -k
```
On success, it will produce an o/p
```
{
  "responseHeader":{
    "zkConnected":true,
    "status":0,
    "QTime":0,
    "params":{
      "q":"*:*",
      "indent":"true",
      "wt":"json"}},
  "response":{"numFound":2,"start":0,"docs":[
      {
        "id":"TestDoc1",
        "title_s":"test1",
        "_version_":1593556033717927936},
      {
        "id":"TestDoc2",
        "title_s":"another test",
        "_version_":1593556033727365120}]
  }}
```
