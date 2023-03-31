# spring-boot-kub
hello world for running spring boot docker image on kubernetes
##Steps

- mkdir spring-boot-kub
- cd spring-boot-kub
- curl https://start.spring.io/starter.tgz -d dependencies=webflux,actuator | tar -xzvf -
docker build -t balaji142857/spring-kub-demo .

[//]: # ( dockerfile - using gradle)

[//]: # (FROM eclipse-temurin:17-jdk-alpine)

[//]: # (VOLUME /tmp)

[//]: # (COPY build/libs/*.jar app.jar)

[//]: # (ENTRYPOINT ["java","-jar","/app.jar"])


- docker run -p 8080:8080 --name gs-spring-boot-k8s -t balaji142857/spring-kub-demo .
- curl http://localhost:8080/actuator/health; echo
- docker push balaji142857/spring-kub-demo

- kubectl create deployment demo --image=balaji142857/spring-kub-demo --dry-run -o=yaml > deployment.yaml
- echo --- >> deployment.yaml
- kubectl create service clusterip demo --tcp=8080:8080 --dry-run -o=yaml >> deployment.yaml

- kubectl apply -f deployment.yaml

[//]: # (deployment.apps/demo created)

[//]: # (service/demo created)
