FROM orax/alpine-armhf:3.5
MAINTAINER Mike Geiger <NOOP@chstech.org>

RUN apk update \
 && apk upgrade \
 && apk add --update \
      bash \
      build-base \
      curl \
      dumb-init \
      libffi-dev \
      linux-headers \
      musl \
      openssl-dev \
      py2-pip \
      python \
      python-dev \
      ruby \
      ruby-bundler \
      ruby-irb\
      ruby-rdoc \
      wget \
 && rm -rf /var/cache/apk/* \
 && mkdir /geemusic

COPY . /geemusic
WORKDIR /geemusic

RUN pip install -r requirements.txt \
 && gem install bundler \
 && gem install foreman

EXPOSE 5000

# Make sure to run with the GOOGLE_EMAIL, GOOGLE_PASSWORD, and APP_URL environment vars!
ENTRYPOINT ["/usr/bin/dumb-init"]
CMD ["foreman", "start"]
