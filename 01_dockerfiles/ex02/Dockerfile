FROM ruby

RUN mkdir -p /opt/
WORKDIR /opt/

RUN gem install rails bundler
RUN gem install rails

#configure yarn package repository
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    sqlite3 \
    nodejs \
    yarn \
    git

RUN rails new app
WORKDIR /opt/app/

RUN bundle update && bundle install

#rake is a utility built into Ruby and Rails to manage database changes
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed

#run
#docker build -t ft-rails:on-build .
#mkdir app
#{ echo "FROM ft-rails:on-build"; echo "EXPOSE 3000"; echo "CMD [ \"rails\", \"s\", \"-b\", \"0.0.0.0\", \"-p\",\"3000\" ]";} > app/Dockerfile
#docker build -t ex02 ./app
#docker run --name ex02 --rm -p 3000:3000 ex02
