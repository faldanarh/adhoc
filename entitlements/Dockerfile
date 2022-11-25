FROM registry.redhat.io/rhel9/python-39:latest

USER root

COPY ./etc-pki-entitlement /etc/pki/entitlement
COPY ./rhsm-conf /etc/rhsm
COPY ./rhsm-ca /etc/rhsm/ca

RUN ls /etc/pki/entitlement

# Delete /etc/rhsm-host to use entitlements from the build container
RUN rm -f /etc/rhsm-host

# Check enabled repositories
#RUN yum repolist all
RUN dnf install --enablerepo=rhel-9-for-x86_64-appstream-rpms -y golang && \
    # Remove entitlements and Subscription Manager configs
    rm -rf /etc/pki/entitlement && \
    rm -rf /etc/rhsm
#RUN yum install -y golang

# OpenShift requires images to run as non-root by default
USER 1001

ENTRYPOINT ["/bin/bash"]
