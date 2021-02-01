FROM ruby:2.1.2

ENV LANG C.UTF-8

RUN mkdir -p /isucon5-bench
COPY . /isucon5-bench/
WORKDIR /isucon5-bench

RUN bundle install --path vendor/bundle --binstubs=vendor/bundle/bin

CMD bundle exec ruby agent.rb
