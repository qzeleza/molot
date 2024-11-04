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
# 		1. 	https://github.com/openwrt/buildbot/blob/master/docker/buildworker/Dockerfile
# 
#----------------------------------------------------------------------------------

    FROM docker.io/debian:stable-slim
    ARG USER_NAME
    
    RUN apt-get -qy install locales
    RUN locale-gen --no-purge en_US.UTF-8
    
    ENV LC_ALL en_US.UTF-8
    ENV GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'
    
    RUN apt-get update && apt-get install --no-install-recommends --no-install-suggests --yes \
        'build-essential' \
        'ca-certificates' \
        'clang' \
        'flex' \
        'bison' \
        'g++' \
        'gawk' \
        'gcc-multilib' \
        'gettext' \
        'git' \
        'libncurses5-dev' \
        'libssl-dev' \
        'python3-distutils' \
        'rsync' \
        'unzip' \
        'zlib1g-dev' \
        'file' \
        'wget' \
      && \
      rm -f -r '/var/lib/apt/' && \
      rm -f -r '/var/cache/apt/' && \
      useradd -m -s '/bin/bash' -U 'buildbot' \
      echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers \
      useradd -c "Пользователь для сборки образов Openwrt " -m -d /home/${USER_NAME} -G sudo -s /bin/bash ${USER_NAME}
    
    USER ${USER_NAME}
    WORKDIR /home/${USER_NAME} 
    ENV HOME=/home/${USER_NAME}
    