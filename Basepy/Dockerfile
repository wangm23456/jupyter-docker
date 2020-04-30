# FROM continuumio/miniconda3:4.8.2
FROM python:3.7

ADD pip-base.txt requirements.txt

RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak && \
    echo "deb http://mirrors.163.com/debian/ jessie main non-free contrib" >/etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/debian/ jessie-proposed-updates main non-free contrib" >>/etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/debian/ jessie main non-free contrib" >>/etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/debian/ jessie-proposed-updates main non-free contrib" >>/etc/apt/sources.list

RUN mkdir /root/.pip && \
    touch /root/.pip/pip.conf && \
    echo "[global]" > /root/.pip/pip.conf && \
    echo "index-url=https://mirrors.163.com/pypi/simple/" >> /root/.pip/pip.conf

ADD condarc /root/.condarc

#设置时区
RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo 'Asia/Shanghai' >/etc/timezone

RUN pip install --upgrade setuptools pip \
    && pip install --no-cache-dir -r requirements.txt

# RUN conda install --yes --file requirements.txt

CMD [ "/bin/bash" ]