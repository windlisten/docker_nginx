From wenzhi/centos7-systemd
MAINTAINER wenzhi
ADD ./files /usr/local
RUN cd /usr/local && \
    tar -zxvf nginx-config.tgz && \
    tar -zxvf nginx-1.12.1.tar.gz && \
    tar -zxvf ngx_http_substitutions_filter_module.tgz && \
    yum install pcre-devel openssl-devel zlib-devel curl yum-utils geoip-devel -y && \
    yum -y install  automake autoconf libtool make zlib pcre openssl && \
    yum -y install gcc gcc-c++ && \
    mkdir -p /var/cache/nginx/client_temp && \
    mkdir -p /var/cache/nginx/proxy_temp && \
    mkdir -p /var/cache/nginx/fastcgi_temp && \
    mkdir -p /var/cache/nginx/uwsgi_temp && \
    mkdir -p /var/cache/nginx/scgi_temp && \
    cd /usr/local/nginx-1.12.1 && \
    ./configure --prefix=/etc/nginx --sbin-path=/usr/sbin/nginx --modules-path=/usr/lib64/nginx/modules --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --pid-path=/var/run/nginx.pid --lock-path=/var/run/nginx.lock --http-client-body-temp-path=/var/cache/nginx/client_temp --http-proxy-temp-path=/var/cache/nginx/proxy_temp --http-fastcgi-temp-path=/var/cache/nginx/fastcgi_temp --http-uwsgi-temp-path=/var/cache/nginx/uwsgi_temp --http-scgi-temp-path=/var/cache/nginx/scgi_temp --user=nginx --group=nginx --with-compat --with-file-aio --with-threads --with-http_addition_module --with-http_auth_request_module --with-http_dav_module --with-http_flv_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_mp4_module --with-http_random_index_module --with-http_realip_module --with-http_secure_link_module --with-http_slice_module --with-http_ssl_module --with-http_stub_status_module --with-http_sub_module --with-http_v2_module --with-mail --with-mail_ssl_module --with-stream --with-stream_realip_module --with-stream_ssl_module --with-stream_ssl_preread_module --with-cc-opt='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector-strong --param=ssp-buffer-size=4 -grecord-gcc-switches -m64 -mtune=generic -fPIC' --with-ld-opt='-Wl,-z,relro -Wl,-z,now -pie' --add-module=/usr/local/ngx_http_substitutions_filter_module --with-http_geoip_module && \
    make -j3 && make install && \
    groupadd nginx && \
    useradd nginx -g nginx  && \
    rm -rf /etc/nginx/* && \
    mv /usr/local/nginx-config/* /etc/nginx/ && \
    mv /usr/local/nginx.init /etc/init.d/nginx && \
    chmod a+x /etc/init.d/nginx && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    RUN yum clean all 

CMD tail -f /dev/null

EXPOSE 80
