FROM ruby:2.3.0

# install packege
RUN apt-get update && \
    apt-get install -y git \
    vim \
    protobuf-compiler \
    autoconf \
    bison \
    build-essential \
    libssl-dev \
    libyaml-dev \
    libreadline6-dev \
    zlib1g-dev \
    libncurses5-dev \
    mysql-client

# railsの最新バージョンがこれやらないと入ってない
# gem update --systemは上手くいかなかったので
#RUN gem install rubygems-update
#RUN update_rubygems
#RUN gem install bundler

ENV LANG C.UTF-8

RUN mkdir /base01

WORKDIR /tmp
COPY Gemfile Gemfile
COPY Gemfile.lock Gemfile.lock
RUN bundle install

ADD . /base01
WORKDIR /base01

# git config setting
RUN git config --global user.name "k-nishiyama"
RUN git config --global user.email k-nishiyama@bns-g.com
