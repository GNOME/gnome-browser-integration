ARG PYTHON_VERSION

FROM docker.io/python:$PYTHON_VERSION
SHELL ["/bin/bash", "-exo", "pipefail", "-c"]

COPY requirements.txt /tmp/pip-tmp/

RUN \
    apt-get update ;\
    apt-get -y install \
        bash-completion \
        coreutils \
        git \
        git-gui \
        gitk \
        sudo \
    ;\
    pip --disable-pip-version-check --no-cache-dir install \
        -r /tmp/pip-tmp/requirements.txt \
    ;\
    adduser --disabled-password --gecos '' vscode ;\
    echo "vscode ALL=(root) NOPASSWD: ALL" > /etc/sudoers.d/vscode

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1

ENTRYPOINT [ "/bin/sh" ]
CMD [ "-c", "sleep infinity" ]
