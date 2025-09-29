FROM debian:latest

# Preventing interactive questions
ENV DEBIAN_FRONTEND=noninteractive

# Installing the required packages
RUN apt update && \
    apt install -y \
        openssh-server \
        python3 && \
    mkdir -p /var/run/sshd && \
    echo 'root:DockerPassword123' | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Open SSH port
EXPOSE 22

# Starts the SSH server
CMD ["/usr/sbin/sshd", "-D"]