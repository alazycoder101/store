FROM ruby:3.1.2-slim

RUN apt-get update -qq && \
    apt-get install -yq --no-install-recommends build-essential libpq-dev \
    git nodejs libvips imagemagick

ARG app=/opt/store
WORKDIR $app

ENV RAILS_ROOT=$app \
    RAILS_ENV=${RAILS_ENV:-development}

COPY Gemfile Gemfile.lock ./
RUN gem install bundler && \
    bundle install

COPY . ./
RUN rm -rf log/* && \
    rm -rf tmp/*

ARG REVISION
ENV GIT_REVISION=${REVISION}

EXPOSE 8081
CMD bundle exec puma -b tcp://0.0.0.0:8081 --pidfile /tmp/puma.pid -S /tmp/puma.state --preload --prune-bundler
