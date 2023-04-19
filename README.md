# Observability-Assignment
Observability Assignment for Enterprise SWE class using OpenTelemetry and Jaeager

### To run in WSL2 ubuntu:
1. Clone repo and run `$ npm install` in the root
2. Start docker daemon `$ sudo dockerd`
3. In a new terminal, run mongo in a docker container `$ docker run -d -p 27017:27017 mongo`
4. Run Jaeger in a docker container
  ```bash 
$ docker run -d --name jaeger \
  -e COLLECTOR_ZIPKIN_HOST_PORT=:9411 \
  -p 5775:5775/udp \
  -p 6831:6831/udp \
  -p 6832:6832/udp \
  -p 5778:5778 \
  -p 16686:16686 \
  -p 14250:14250 \
  -p 14268:14268 \
  -p 14269:14269 \
  -p 9411:9411 \
  jaegertracing/all-in-one:1.32
  ```
  5. Run the node app `$ node index.js`
  6. In a new terminal, `$ curl http://localhost:3000/todo`
  7. Look at the trace in the Jaeger UI at http://localhost:16686/
