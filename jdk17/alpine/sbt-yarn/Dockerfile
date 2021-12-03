FROM keyno63/sbt:1.5-jdk17-alpine

RUN set -x \
    && apk add bash curl nodejs \
    && touch ~/.bashrc \
    && curl -o- -L https://yarnpkg.com/install.sh | bash \
    && ln -s "$HOME/.yarn/bin/yarn" /usr/local/bin/yarn

ENV PATH="$HOME/.yarn/bin:$PATH"
