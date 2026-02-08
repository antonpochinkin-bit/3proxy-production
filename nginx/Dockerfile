FROM nginx:alpine

# Копируем конфигурацию
COPY nginx.conf /etc/nginx/nginx.conf

# Создаем статическую страницу для мониторинга
RUN echo '<html><body><h1>Nginx Load Balancer for 3proxy</h1><p><a href="/status">Status</a></p></body></html>' > /usr/share/nginx/html/index.html

EXPOSE 80 18080 11080 13128 11081
