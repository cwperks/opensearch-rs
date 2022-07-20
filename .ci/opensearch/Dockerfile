ARG STACK_VERSION
FROM "opensearchproject/opensearch:$STACK_VERSION"
ARG SECURE_INTEGRATION
ARG opensearch_path=/usr/share/opensearch
ARG opensearch_yml=$opensearch_path/config/opensearch.yml
RUN chmod +x $opensearch_path/plugins/opensearch-security/tools/install_demo_configuration.sh
RUN yes | $opensearch_path/plugins/opensearch-security/tools/install_demo_configuration.sh
RUN echo "plugins.security.filter_securityindex_from_all_requests: true" >> $opensearch_yml
RUN if [ "$SECURE_INTEGRATION" != "true" ] ; then $opensearch_path/bin/opensearch-plugin remove opensearch-security; fi
