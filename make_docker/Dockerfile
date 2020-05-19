FROM heyangguang123/python3:3.7.2
ADD elastalert.tar /opt/
VOLUME /opt/elastalert/config/
VOLUME /opt/elastalert/logs/
VOLUME /opt/elastalert/rule/
RUN yum -y install epel-release
RUN yum -y install gcc gcc+
#RUN pip install --upgrade pip
#RUN pip install --upgrade setuptools==30.1.0
RUN yum install gcc libffi-devel python3-devel openssl-devel -y
RUN pip3 install -r /opt/elastalert/requirements.txt
RUN pip3 install pyOpenSSL
RUN cd /opt/elastalert/ && python3 setup.py install
ENV RULE_NAME rule.yml
ENV LOG_NAME rule.log
CMD cd /opt/elastalert/ && python3 -m elastalert.elastalert --verbose --config /opt/elastalert/config.yaml --rule /opt/elastalert/rule/$RULE_NAME >> /opt/elastalert/logs/$LOG_NAME 2>&1