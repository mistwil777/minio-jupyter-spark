FROM quay.io/jupyter/pyspark-notebook:2025-11-25

USER root

RUN mkdir -p /opt/conda/lib/python3.*/site-packages/pyspark/jars && \
    chmod a+rwx /opt/conda/lib/python3.*/site-packages/pyspark/jars

RUN apt-get update && apt-get install -y curl && \
    curl -fSL https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-aws/3.3.4/hadoop-aws-3.3.4.jar -o /opt/conda/lib/python3.*/site-packages/pyspark/jars/hadoop-aws-3.3.4.jar && \
    curl -fSL https://repo1.maven.org/maven2/com/amazonaws/aws-java-sdk-bundle/1.12.262/aws-java-sdk-bundle-1.12.262.jar -o /opt/conda/lib/python3.*/site-packages/pyspark/jars/aws-java-sdk-bundle-1.12.262.jar && \
    chmod a+r /opt/conda/lib/python3.*/site-packages/pyspark/jars/*.jar

USER $NB_UID
