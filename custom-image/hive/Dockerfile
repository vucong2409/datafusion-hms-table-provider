FROM apache/hive:3.1.3

USER root
# Get some package for easier debugging.
RUN apt update && apt install -yq wget curl vim

# Get newer JDBC driver (to support new encryption scheme of PostgreSQL)
RUN wget https://repo1.maven.org/maven2/org/postgresql/postgresql/42.2.28.jre7/postgresql-42.2.28.jre7.jar -O /opt/hive/lib/postgresql-42.2.28.jre7.jar
RUN rm -f postgresql-9.4.1208.jre7.jar
RUN chown -R root:staff /opt/hive/lib/

# Get hadoop-aws
RUN wget https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/3.1.0/hadoop-aws-3.1.0.jar -O  /opt/hadoop/share/hadoop/yarn/hadoop-aws-3.1.0.jar
RUN wget https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk-bundle/1.11.271/aws-java-sdk-bundle-1.11.271.jar -O /opt/hadoop/share/hadoop/yarn/aws-java-sdk-bundle-1.11.271.jar
RUN chown -R hive:hive /opt/hadoop/share/hadoop/yarn/

# Switch back to hive user
USER hive
