FROM ruby:2.5.1-slim-stretch
MAINTAINER Dave Silva <docker@dmsilva.com>

RUN groupadd --gid 99 app_user \
&& useradd --gid 99 --uid 99 --system app_user
RUN mkdir -p /usr/app /home/app_user && chown app_user /usr/app /home/app_user
WORKDIR /usr/app

RUN apt-get update && apt-get -y install build-essential sqlite3 libsqlite3-dev

USER app_user

COPY --chown=app_user Gemfile .
COPY --chown=app_user Gemfile.lock .

RUN bundle install

COPY --chown=app_user main.rb .

CMD [ "ruby", "main.rb" ]
