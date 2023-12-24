FROM centos:7

RUN yum update -y && \
    yum install -y python3 python3-pip && \
    yum clean all && \
    rm -rf /var/cache/yum
RUN pip3 install flask flask-jsonpify flask-restful

COPY python-api.py /opt/python_api/python-api.py

EXPOSE 5290
CMD ["python3", "/opt/python_api/python-api.py"]
