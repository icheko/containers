FROM registry.access.redhat.com/ubi8/nodejs-14:1

USER root

# Setup to download updates from RH
COPY ./rhsm-entitlement /etc/pki/entitlement
RUN rm /etc/rhsm-host

# Install Chrome
RUN dnf upgrade --refresh rpm glibc && \
    curl https://dl.google.com/linux/linux_signing_key.pub -O && rpm --import linux_signing_key.pub && \
    curl https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm -O && rpm --checksig -v google-chrome-stable_current_x86_64.rpm && \
    dnf install -y google-chrome-stable_current_x86_64.rpm && \
    rm -rfv /etc/pki/entitlement && \
    rm -fv google-chrome-stable_current_x86_64.rpm && \
    rm -fv linux_signing_key.pub

USER 1001