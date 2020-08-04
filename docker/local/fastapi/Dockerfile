FROM jetblackpope/pybuntu:3.8-focal

ARG DEBIAN_FRONTEND=noninteractive
ARG USERNAME=code
ARG USER_UID=1000
ARG USER_GID=$USER_UID
ENV PIPENV_MAX_SUBPROCESS 16

ARG USERNAME=code
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN python -m pip install pip pipenv apt-select --upgrade

RUN apt-select \
    && cp /etc/apt/sources.list /etc/apt/sources.list.backup \
    && mv sources.list /etc/apt/

RUN apt-get update

RUN apt-get install --no-install-recommends --no-install-suggests -y \
    apt-utils \
    dialog \
    ca-certificates

RUN apt-get install --no-install-recommends --no-install-suggests -y \
    git \
    gpg \
    openssh-client \
    less \
    iproute2 \
    procps \
    curl \
    wget \
    lsb-release \
    build-essential \
    libssl1.1 \
    libpq-dev \
    postgresql-client \
    htop

# RUN groupadd --gid $USER_GID $USERNAME \
#     && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME -s /bin/bash \
#     && apt-get install --no-install-recommends --no-install-suggests -y sudo \
#     && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
#     && chmod 0440 /etc/sudoers.d/$USERNAME

RUN echo "export PROMPT_COMMAND='history -a'" >> "/root/.bashrc" \
    && echo "export HISTFILE=/commandhistory/.bash_history" >> "/root/.bashrc"

# USER $USERNAME

WORKDIR /code