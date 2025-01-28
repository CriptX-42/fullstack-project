---
Created: 2025-01-27
tags:
  - Construir
  - Aprofundar
---
### Um exemplo de dockerfile

```
//Pegando o maven e chamando ele de build
FROM maven:3.8.4-jdk-8 AS build  

//Copiamos tudo em src e pom
COPY src /app/src  
COPY pom.xml /app  

//Vamos pra dentro de APP e executamos o mvn
WORKDIR /app  
RUN mvn clean install  

//Instalamos o JRE
FROM openjdk:8-jre-alpine  

//Copiamos o arquivo de build para o /app/app.jar
COPY --from=build /app/target/spring-boot-2-hello-world-1.0.2-SNAPSHOT.jar /app/app.jar  

//Voltamos a pasta app
WORKDIR /app  

//Expor a porta 80
EXPOSE 8080  

//Colocamos os comandos a ser executados ao iniciar o container
CMD ["java", "-jar", "app.jar"]
```