FROM httpd:bullseye

ADD tomcat-connectors-1.2.48-src.tar /
COPY mod_jk.conf workers.properties /
WORKDIR /tomcat-connectors-1.2.48-src/native
RUN ls -al
RUN ./buildconf.sh
RUN ./configure --with-apxs=/usr/local/apache2/bin/apxs

RUN make && make install

RUN mv /mod_jk.conf /usr/local/apache2/conf/extra/
RUN mv /workers.properties /usr/local/apache2/conf/

RUN echo "LoadModule jk_module /usr/local/apache2/modules/mod_jk.so" >> /usr/local/apache2/conf/httpd.conf
RUN echo "Include conf/extra/mod_jk.conf" >> /usr/local/apache2/conf/httpd.conf

EXPOSE 80/HTTP
CMD ["httpd-foreground"]
