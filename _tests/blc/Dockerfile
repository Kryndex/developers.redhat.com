FROM test-base:2.3.0

WORKDIR /tmp
RUN yum install -y bzip2 fontconfig freetype freetype-devel fontconfig-devel libstdc++ && \
    wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2 && \
    mkdir -p /opt/phantomjs && \
    tar -xjvf /tmp/phantomjs-2.1.1-linux-x86_64.tar.bz2 -C /opt/phantomjs/ && \
    cp /opt/phantomjs/phantomjs-2.1.1-linux-x86_64/bin/phantomjs /usr/bin/phantomjs

COPY Gemfile Gemfile.lock ./
RUN bundle install -j 10

RUN groupadd -g 1000 blc
RUN useradd -g blc -m -s /bin/bash -u 1000 blc
USER blc
WORKDIR /home/blc
