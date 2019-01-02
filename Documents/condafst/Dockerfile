FROM ubuntu:18.04

RUN apt-get update && apt-get install -y apt-utils 

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential gcc g++ libsqlite3-dev libpython3-dev python3-dev graphviz wget vim ssh make vim zlib1g-dev libbz2-dev libssl-dev man libreadline-dev libreadline-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev python3 unzip

RUN wget https://repo.anaconda.com/archive/Anaconda3-5.2.0-Linux-x86_64.sh
RUN bash Anaconda3-5.2.0-Linux-x86_64.sh -b
RUN rm Anaconda3-5.2.0-Linux-x86_64.sh

# Set path to conda
ENV PATH /root/anaconda3/bin:$PATH

RUN ldconfig

RUN pip install --upgrade pip

RUN pip install --upgrade graphviz pystache msgpack

RUN cd /tmp && wget http://www.openfst.org/twiki/pub/FST/FstDownload/openfst-1.6.9.tar.gz && tar xzvf openfst-1.6.9.tar.gz && cd openfst-1.6.9 && ./configure --enable-far --enable-pdt --enable-mpdt && make && make install && ldconfig
RUN rm -rf /tmp/openfst-1.6.9.tar.gz

RUN cd /tmp && wget https://github.com/alexknvl/pyfst/archive/master.zip && unzip master.zip
RUN cd /tmp/pyfst-master && python setup.py build
RUN cd /tmp/pyfst-master && python setup.py install
RUN ldconfig
RUN rm -rf /tmp/master.zip


