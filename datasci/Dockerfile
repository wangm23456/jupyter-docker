# FROM continuumio/miniconda3:4.8.2
FROM jupyter/datascience-notebook

USER root

ADD requirements.txt requirements.txt

RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo 'Asia/Shanghai' >/etc/timezone

RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak && \
    echo "deb http://mirrors.163.com/debian/ jessie main non-free contrib" >/etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/debian/ jessie-proposed-updates main non-free contrib" >>/etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/debian/ jessie main non-free contrib" >>/etc/apt/sources.list && \
    echo "deb-src http://mirrors.163.com/debian/ jessie-proposed-updates main non-free contrib" >>/etc/apt/sources.list

RUN mkdir /home/jovyan/.pip && \
    touch /home/jovyan/.pip/pip.conf && \
    echo "[global]" > /home/jovyan/.pip/pip.conf && \
    echo "index-url=https://mirrors.163.com/pypi/simple/" >> /home/jovyan/.pip/pip.conf

RUN pip install --upgrade setuptools pip \
    && pip install --no-cache-dir -r requirements.txt

# ADD condarc /home/jovyan/.condarc
RUN conda update --all --yes

RUN mkdir /data

# RUN conda install --yes --file requirements.txt

CMD [ "/bin/bash" ]