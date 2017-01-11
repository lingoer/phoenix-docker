FROM alpine
MAINTAINER I DONT <really@maintain.it>
ENV ELIXIR_VERSION 1.4.0
RUN apk add --no-cache inotify-tools erlang erlang-crypto erlang-syntax-tools erlang-parsetools erlang-dev wget ca-certificates nodejs
RUN apk add --no-cache erlang-inets erlang-ssl erlang-public-key erlang-asn1 erlang-sasl erlang-erl-interface erlang-dev
RUN mkdir -p /opt/elixir-${ELIXIR_VERSION}/ && \
    wget https://github.com/elixir-lang/elixir/releases/download/v${ELIXIR_VERSION}/Precompiled.zip && \
    unzip Precompiled.zip -d /opt/elixir-${ELIXIR_VERSION}/ && \
    rm Precompiled.zip
ENV PATH $PATH:/opt/elixir-${ELIXIR_VERSION}/bin
RUN mix local.hex --force
RUN mix local.rebar --force
RUN mix archive.install --force https://github.com/phoenixframework/archives/raw/master/phoenix_new.ez
WORKDIR /app

