### exec bash container
docker exec -it test_db_1 bash
##### user root
docker exec -itu0 test_db_1 bash
### IP container
docker inspect  casadiluce_db | grep IPAddress
### Format output
docker ps  --format "table {{.ID}}\t{{.Names}}\t{{.Ports}}"
docker ps -a --format "{{.ID}}: {{.Names}}\t{{.Size}}"
docker images --format "{{.ID}}\t{{.Size}}\t{{.Repository}}" | sort -k 2
### IP xdebug ubuntu
 172.17.0.1
