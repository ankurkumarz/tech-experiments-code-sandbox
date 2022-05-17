# IBM MQ Consumer Sender App

This utility has 2 REST endpoints:
- /send: to send a message to the MQ queue
- /receive: to receive a message from the MQ queue

## Run the utility
- Run IBM MQ locally
```
docker run -e LICENSE=accept -e MQ_QMGR_NAME=QM1 --publish 1414:1414 --detach ibmcom/mq
```


```
mvn package

```
- Send & receive message to the MQ queue
```
curl -k http://localhost:8080/send
curl -k http://localhost:8080/recv
``` 
- To check message in MQ
```
docker exec -it <container-id> bash
cd /opt/mqm/samp/bin
./amqscbf DEV.QUEUE.1
dmpmqmsg -i QM1 -ds -m QM1
```

## References
- https://www.ibm.com/docs/en/mq-appliance/9.2?topic=client-browsing-message-queue
- https://developer.ibm.com/tutorials/mq-jms-application-development-with-spring-boot/