# FROM jaimec21/opencv-docker:latest

# RUN apt-get update && apt-get install -y

# # Install boost
# RUN apt-get install -y libboost-all-dev

# # Install Eigen
# RUN apt-get update && apt-get install -y libeigen3-dev

# RUN echo "LIBGL_ALWAYS_INDIRECT=0" >> ~/.bashrc


FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    build-essential \
    gcc g++ gdb\
    git \
    python3 python3-pip python3-venv

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=${USER_UID}
RUN groupadd --gid ${USER_GID} ${USERNAME} \
    && useradd -m -s /bin/bash --uid ${USER_UID} --gid ${USER_GID} ${USERNAME} \
    && apt-get update && apt-get install -y sudo \
    && echo "${USERNAME} ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/${USERNAME} \
    && chmod 0440 /etc/sudoers.d/${USERNAME}

USER ${USERNAME}
WORKDIR /workspace
RUN git config --global --add safe.directory /workspace