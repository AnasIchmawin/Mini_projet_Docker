FROM python:3.8-buster

LABEL maintainer="Anas Ichmawin anasichmawin87@gmail.com, Mohamed-Amine Fatih fatihmohamedamine5@gmail.com, Mourad Imani imanimourad92@gmail.com"

WORKDIR /

RUN apt update -y && \
    apt install -y python3-dev libsasl2-dev libldap2-dev libssl-dev 
    
COPY student_age.py requirements.txt /

RUN pip3 install -r /requirements.txt

RUN mkdir -p /data

VOLUME ["/data"]

EXPOSE 5000

CMD ["python3", "./student_age.py"]
