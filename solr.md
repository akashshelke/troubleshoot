1. ssh login to solr server and kinit with solr keytab 
2.delete ranger_audits collection
# curl -iv --negotiate -u: "http://$(hostname -f):8886/solr/admin/collections?action=DELETE&name=ranger_audits&async=delete_ranger_audits" 

3.stop infra solr

4.go to each infra solr node and delete the collection folder manually if present

5.start infra solr

6.create collections 
 curl -iv --negotiate -u : "http://`hostname -f`:8886/solr/admin/collections?action=CREATE&name=ranger_audits&numShards=9&replicationFactor=2&collection.configName=ranger_audits&maxShardsPerNode=20
#curl --negotiate -u: "http://$SOLR_HOST:8886/solr/ranger_audits/update?commit=true" -H "Content-Type:text/xml" --data-binary "<delete><query>evtTime:[* TO NOW-15DAYS]</query></delete>" 

Hdfs audit to hive
https://risdenk.github.io/2018/03/23/apache-ranger-hive-over-hdfs-audit-logs.html
