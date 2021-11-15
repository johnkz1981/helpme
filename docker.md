### exec bash container
docker exec -it test_db_1 bash
##### user root
docker exec -itu0 test_db_1 bash
### IP container
docker inspect  casadiluce_db | grep IPAddress
### Format output
docker ps  --format "table {{.ID}}\t{{.Names}}\t{{.Ports}}"
### IP xdebug ubuntu
 172.17.0.1
