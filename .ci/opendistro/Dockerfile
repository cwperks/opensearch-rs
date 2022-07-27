ARG STACK_VERSION
FROM "amazon/opendistro-for-elasticsearch:$STACK_VERSION"
ARG SECURE_INTEGRATION
ARG es_path=/usr/share/elasticsearch
ARG es_yml=$es_path/config/elasticsearch.yml

RUN if [ "$SECURE_INTEGRATION" == "true" ] ; then chmod +x $es_path/plugins/opendistro_security/tools/install_demo_configuration.sh; fi
RUN if [ "$SECURE_INTEGRATION" == "true" ] ; then yes | $es_path/plugins/opendistro_security/tools/install_demo_configuration.sh; fi
RUN if [ "$SECURE_INTEGRATION" == "true" ] ; then echo "opendistro_security.allow_default_init_securityindex: false" >> $es_yml; fi
RUN if [ "$SECURE_INTEGRATION" != "true" ] ; then $es_path/bin/elasticsearch-plugin remove opendistro_security; fi