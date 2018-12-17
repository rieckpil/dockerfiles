# Docker image for Oracle XE on Oracle Linux

Available versions:

* Oracle XE 18 on Oracle Linux
* Template from [fuzziebrain](https://github.com/fuzziebrain/docker-oracle-xe)
* `.rpm` has to be downloaded to `files/` ([Download](https://www.oracle.com/technetwork/database/database-technologies/express-edition/downloads/index.html))
* `.sh` files has to be `LF` as end of line sequence

## Running the container

```bash
docker run -d \
  -p 32118:1521 \
  -p 35518:5500 \
  --name=oracle-xe \
  --volume ~/docker/oracle-xe:/opt/oracle/oradata \
  --network=oracle_network \
  rieckpil/oracle-xe:18c

docker run -d \
  -p 32118:1521 \
  -p 35518:5500 \
  --name=oracle-xe \
  rieckpil/oracle-xe:18c
  

# As this takes a long time to run you can keep track of the initial installation by running:
docker logs oracle-xe

docker stop -t 200 oracle-xe
```