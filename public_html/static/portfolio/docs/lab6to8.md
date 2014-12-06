###Lab 6/7/8 -Geo IP Location Map
```
#!/bin/bash
# geoip2
# sassenbergm

function pull_access() {
  xz -d -c  /home/acc*.xz | awk '{print $1}' | sort | uniq -u > ~/inclass/geoip1.tmp
  sort -u /home/access_log | cut -f1 -d" " |uniq | >> ~/inclass/geoip1.tmp
}

function ip_dbget() {
  ipaddr=$(cat ~/inclass/geoip1.tmp)

  for x in $ipaddr
  do
   location=$(curl -s http://freegeoip.net/csv/$x)
   echo $location >> ~/inclass/ip_latlong.tmp
  done
}

function sql_dbget() {
  cat ip_latlong.tmp | tr ',' '|' > ip_latlong.log

  sqlite3 ipvisitors.sqlite < mkiptbl.sql3
  echo ".import ip_latlong.log visitors" | sqlite3 ipvisitors.sqlite

pull_access
ip_dbget
sql_dbget
```

