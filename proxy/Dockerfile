FROM jwilder/nginx-proxy
RUN mkdir -p /etc/nginx/vhost.d; \
	{ \      
      echo 'proxy_http_version 1.1;'; \
      echo 'proxy_set_header Upgrade $http_upgrade;'; \
      echo 'proxy_set_header Connection "Upgrade";'; \
    } > /etc/nginx/vhost.d/default_location       