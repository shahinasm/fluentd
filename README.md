<source>
@type tail
path /tmp/access_log-20170205
pos_file /tmp/grock1
<parse>
@type grok
grok_pattern %{IP:ip_address}
</parse>
tag grokked_log
</source>
<match grokked_log>
@type elasticsearch
logstash_format false
host 192.168.1.36 #(optional; default="localhost")
port 9200 #(optional; default=9200)
index_name grok1 #(optional; default=fluentd)
type_name log #(optional; default=fluentd)
</match>


error getting is:-
2017-02-09 11:14:31 +0530 [error]: #0  error_class=NameError error="uninitialized constant Fluent::Plugin::RegexpParser"


i need to use grok pattern instead regular expressions


my log file

vi access_log-20170205

192.168.0.204 - - [02/Feb/2017:16:45:34 +0530] "GET /browserconfig.xml HTTP/1.1" 404 294 "-" "Mozilla/5.0 (Windows NT 6.3; Win64; x64; Trident/7.0; rv:11.0) like Gecko"
192.168.0.204 - - [02/Feb/2017:17:47:01 +0530] "GET /browserconfig.xml HTTP/1.1" 404 294 "-" "Mozilla/5.0 (Windows NT 6.3; Win64; x64; Trident/7.0; rv:11.0) like Gecko"
