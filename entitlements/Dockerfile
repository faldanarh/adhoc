FROM registry.redhat.io/rhel8/python-38:latest

USER root

COPY ./etc-pki-entitlement /etc/pki/entitlement

RUN ls /etc/pki/entitlement
RUN ls /etc/yum.repos.d

# Delete /etc/rhsm-host to use entitlements from the build container
RUN rm -f /etc/rhsm-host

# Check enabled repositories
#RUN yum repolist all
RUN dnf install --enablerepo=rhel-8-for-x86_64-appstream-rpms -y golang
#RUN yum install -y golang

# OpenShift requires images to run as non-root by default
USER 1001

ENTRYPOINT ["/bin/bash"]
