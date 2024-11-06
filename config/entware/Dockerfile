#----------------------------------------------------------------------------------
#
#   Проект: Молот [molot]
# 
#   Файл сборки среды сборки Entware 
#   Используйтеся в функции создания образа Entware в файле build.me
# 
#   Автор       : Железа
#   Email       : dev@zeleza.ru
#   Лицензия    : Apache Версия 2.0
#
#   Создан      : 21 октября 2024 год
#   Обновлен    : 30 октября 2024 год
# 
# 	Источники
# 		1.	https://github.com/Entware/docker/blob/bc5db21f378a930af81c9b477828fd6db1aa329d/Dockerfile
# 		2. 	https://github.com/openwrt/buildbot/blob/master/docker/buildworker/Dockerfile
# 
#----------------------------------------------------------------------------------

FROM	debian:11

ARG	DEBIAN_FRONTEND=noninteractive
ARG USER_NAME

RUN \
    apt-get update && \
    apt-get install -y \
    build-essential \
    ccache \
    curl \
    gawk \
    g++-multilib \
    gcc-multilib \
    genisoimage \
    git-core \
    gosu \
    libdw-dev \
    libelf-dev \
    libssl-dev \
    libncurses5-dev \
    locales \
    dialog \
    mc \
    jq \
    pv \
    nano \
    pwgen \
    python \
    python3 \
    python3-pip \
    qemu-utils \
    rsync \
    signify-openbsd \
    subversion \
    sudo \
    swig \
    unzip \
    iputils-ping \
    wget \
    file \
    zstd && \
    apt-get clean && \
    localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8 && \
    cp /usr/share/zoneinfo/Europe/Moscow /etc/localtime

RUN pip3 install -U pip
RUN pip3 install \
    pyelftools \
    pyOpenSSL \
    service_identity

ENV LANG=en_US.utf8

RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
RUN useradd -c "Пользователь для сборки образов Entware " -m -d /home/${USER_NAME} -G sudo -s /bin/bash ${USER_NAME}

USER ${USER_NAME}
WORKDIR /home/${USER_NAME} 
ENV HOME=/home/${USER_NAME}
