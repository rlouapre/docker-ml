FROM centos:centos6

MAINTAINER Richard Louapre <richard.louapre@marklogic.com>

#ENV ML_VERSION 7.0-4.3
# ENV ML_RPM_FILE MarkLogic-${ML_VERSION}.x86_64.rpm
ENV ML_RPM_FILE MarkLogic.rpm
#ENV ML_REST_PARAMS t=dYvXoJ1ejkujcVU8IXVTz1&email=richard.louapre%40gmail.com
#ENV ML_DOWNLOAD_URL https://developer.marklogic.com/download/binaries/7.0/${ML_RPM_FILE}?${ML_REST_PARAMS}

# RUN yum -y update && yum clean all

# Download ML rpm
ADD ${ML_RPM_FILE} /tmp/${ML_RPM_FILE}
#RUN curl -k -L -o /tmp/${ML_RPM_FILE} ${ML_DOWNLOAD_URL}

# Install MarkLogic, Python
# RUN yum -y update && yum -y install \
RUN yum -y install \
  /tmp/${ML_RPM_FILE} \
  python-setuptools 

# Install, Supervisor
RUN easy_install supervisor
ADD supervisord.conf /etc/supervisord.conf

# Clean up
RUN yum clean all && rm -rf /tmp/*

WORKDIR /
# Expose MarkLogic admin
EXPOSE 8000 8001 8002
# Run Supervisor
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"] 
