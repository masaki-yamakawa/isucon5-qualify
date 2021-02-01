FROM ruby:2.1.2

ENV LANG C.UTF-8

RUN mkdir -p /isucon5-eventapp
COPY . /isucon5-eventapp/
WORKDIR /isucon5-eventapp

RUN bundle install --path vendor/bundle --binstubs=vendor/bundle/bin

RUN mkdir -p /tmp/isucon/isucon5-qualify/eventapp
RUN sed -i -e 's/home/tmp/g' unicorn_config.rb

EXPOSE 8080
CMD bundle exec unicorn -c ./unicorn_config.rb
