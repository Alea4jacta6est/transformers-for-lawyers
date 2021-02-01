FROM ubuntu:latest
ENV TZ=Europe/Kiev
WORKDIR /
RUN apt-get update \
  && apt-get install -y python3-pip python3-dev \
  && cd /usr/local/bin \
  && ln -s /usr/bin/python3 python \
  && pip3 --no-cache-dir install --upgrade pip \
  && rm -rf /var/lib/apt/lists/*

ADD . /
RUN echo 'alias python3.7=/usr/bin/python3'
RUN python -m pip install -r requirements.txt --cache-dir pip_cache


RUN python -m pip install --pre torch -f https://download.pytorch.org/whl/nightly/cu110/torch_nightly.html --cache-dir /pip_cache


RUN chmod 777 launch.sh
ENTRYPOINT ["./launch.sh"]
