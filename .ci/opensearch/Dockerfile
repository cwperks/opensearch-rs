ARG STACK_VERSION
FROM "opensearchproject/opensearch:$STACK_VERSION"
ARG SECURE_INTEGRATION
ARG opensearch_path=/usr/share/opensearch
ARG opensearch_yml=$opensearch_path/config/opensearch.yml
RUN if [ "$SECURE_INTEGRATION" == "true" ] ; then chmod +x $opensearch_path/plugins/opensearch-security/tools/install_demo_configuration.sh; fi
RUN if [ "$SECURE_INTEGRATION" == "true" ] ; then yes | $opensearch_path/plugins/opensearch-security/tools/install_demo_configuration.sh; fi
RUN if [ "$SECURE_INTEGRATION" == "true" ] ; then echo "plugins.security.allow_default_init_securityindex: false" >> $opensearch_yml; fi
RUN if [ "$SECURE_INTEGRATION" != "true" ] ; then $opensearch_path/bin/opensearch-plugin remove opensearch-security; fi
