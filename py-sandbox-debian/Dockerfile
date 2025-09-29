FROM debian:latest

# Estetään interaktiiviset kysymykset
ENV DEBIAN_FRONTEND=noninteractive

# Asennetaan tarvittavat paketit
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        openssh-server \
        nano \
        python3 \
        ca-certificates && \
    mkdir -p /var/run/sshd && \
    echo 'root:DockerPassword123' | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' /etc/pam.d/sshd && \
    echo "export VISIBLE=now" >> /etc/profile && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Avaa SSH-portti
EXPOSE 22

# Käynnistää SSH-palvelimen
CMD ["/usr/sbin/sshd", "-D"]
