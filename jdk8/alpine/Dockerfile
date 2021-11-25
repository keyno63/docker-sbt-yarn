FROM eed3si9n/sbt:jdk8-alpine

RUN apk add bash curl nodejs
RUN touch ~/.bashrc \
      && curl -o- -L https://yarnpkg.com/install.sh | bash \
      && ln -s "$HOME/.yarn/bin/yarn" /usr/local/bin/yarn \
