    FROM maven:3.9.9-eclipse-temurin-21-jammy as Builder

    WORKDIR /app

    RUN apt update -y && git clone -b docker https://github.com/hkhcoder/vprofile-project.git && cd /app/vprofile-project

    WORKDIR /app/vprofile-project

    RUN mvn clean install


    FROM tomcat:10-jdk21
    
    RUN rm -rf /usr/local/tomcat/webapps/*

    COPY --from=Builder /app/vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war



