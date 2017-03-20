FROM java:8
VOLUME /tmp
COPY entrypoint.sh /entrypoint.sh
COPY target/demo-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["/entrypoint.sh"]
CMD ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
