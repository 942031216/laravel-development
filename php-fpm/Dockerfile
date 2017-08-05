FROM ubuntu:16.04
MAINTAINER chenjiawen <604989282@qq.com>

# 第一步 更换阿里镜像apt源
COPY ./sources.list /etc/apt/sources.list

# 第二步 安装php
RUN apt-get update \
    && apt-get -y install php7.0 \
    && apt-get -y install php7.0-fpm php-mysql php-curl php-dom php-mbstring  php-gd

# 第三步 开启php的扩展
# 覆盖 php-fpm文件 ，1. 关闭 pid 配置 （ 第17行 ）  2. 关闭守护进程  （ 第82行）
COPY  ./php-fpm.conf /etc/php/7.0/fpm/php-fpm.conf

# 覆盖 www.conf文件 1. 修改listen = [::]:9000 （ 第 36 行）
COPY  ./pool.d /etc/php/7.0/fpm/pool.d

# 添加 php.ini 配置信息
COPY  ./conf.d /etc/php/7.0/fpm/conf.d

EXPOSE 9000
CMD ["php-fpm7.0"]