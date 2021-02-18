FROM ruby:2.3.8

ENV LANG C.UTF-8

RUN mkdir -p /isucon5-bench
COPY . /isucon5-bench/
WORKDIR /isucon5-bench

RUN apt-get update && apt-get install -y \
    gradle \
    openjdk-8-jdk

RUN bundle install --path vendor/bundle --binstubs=vendor/bundle/bin

CMD bundle exec ruby agent.rb
