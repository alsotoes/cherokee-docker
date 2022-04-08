FROM alpine:3.15.0
LABEL maintainer="Alvaro Soto alvaro@headup.ws"

WORKDIR /tmp

RUN apk add --no-cache \
        alpine-sdk \
        autoconf \
        automake \
        gettext \
        git \
        libtool \
        openssl \
        openssl-dev \
        python2 \
        linux-headers && \
    openssl req \
            -new \
            -newkey rsa:4096 \
            -days 365 \
            -nodes \
            -x509 \
            -subj "/C=DK/ST=Interstate/L=Capital/O=Acme/OU=Cherokee\ SSL/CN=localhost" \
            -keyout /etc/ssl/key.pem \
            -out /etc/ssl/crt.pem && \
    git clone https://github.com/cherokee/webserver.git . && \
    /usr/bin/libtoolize && \
    aclocal && autoheader && touch ./ChangeLog ./README && autoconf && \
    ./autogen.sh --disable-dependency-tracking --without-php --disable-ipv6 --disable-admin --disable-pam --disable-nls --prefix=/usr --sysconfdir=/etc --localstatedir=/var && \
    autoreconf -iv && \
    make && make install && \
    echo "<p style='text-align:center'>Built from $(git rev-parse --short HEAD) on $(date)</p>" > /version.txt && \
    cat /version.txt >> /var/www/index.html && \
    apk del \
        alpine-sdk \
        autoconf \
        automake \
        gettext \
        git \
        libtool \
        openssl \
        openssl-dev \
        python2 \
        linux-headers && \
    rm -rvf /tmp/*

COPY cherokee.conf /etc/cherokee

EXPOSE 80 443

CMD ["/usr/sbin/cherokee"]
