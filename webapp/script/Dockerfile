FROM ruby:2.3.8

ENV LANG C.UTF-8

RUN mkdir -p /isucon5-datagen
COPY . /isucon5-datagen/
WORKDIR /isucon5-datagen

RUN bundle install --path vendor/bundle --binstubs=vendor/bundle/bin

CMD bundle exec ruby gen.rb
