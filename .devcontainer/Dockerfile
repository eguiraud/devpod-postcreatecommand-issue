FROM ubuntu:22.04

# Create non-superuser: using root as the user in the devcontainer
# causes problems with ownership and permissions of the bind mounts.
# devuser has full sudo powers.
ARG USERNAME=devuser
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME -s /bin/bash -p '$6$xyz$VStsPXzkmjhaciLNxlcaFNiezXAB1uvxc6ZsMo1eBcNw50yRi8zhB1C4y16QJE1gQqyoU2yMY3Q1A7.D6WhJE1' \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME
RUN apt-get install -y git  # for pre-commit

USER $USERNAME
