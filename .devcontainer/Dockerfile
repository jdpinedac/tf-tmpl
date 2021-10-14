# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.202.3/containers/python-3/.devcontainer/base.Dockerfile

# [Choice] Python version (use -bullseye variants on local arm64/Apple Silicon): 3, 3.9, 3.8, 3.7, 3.6, 3-bullseye, 3.9-bullseye, 3.8-bullseye, 3.7-bullseye, 3.6-bullseye, 3-buster, 3.9-buster, 3.8-buster, 3.7-buster, 3.6-buster
ARG VARIANT="3.9-bullseye"
FROM mcr.microsoft.com/vscode/devcontainers/python:0-${VARIANT}

# [Choice] Node.js version: none, lts/*, 16, 14, 12, 10
ARG NODE_VERSION="none"
RUN if [ "${NODE_VERSION}" != "none" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# [Optional] If your pip requirements rarely change, uncomment this section to add them to the image.
# COPY requirements.txt /tmp/pip-tmp/
# RUN pip3 --disable-pip-version-check --no-cache-dir install -r /tmp/pip-tmp/requirements.txt \
#    && rm -rf /tmp/pip-tmp

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
        && apt-get -y install --no-install-recommends emacs-nox=1:26.1+1-3.2+deb10u2 \
        && apt-get clean && rm -rf /var/lib/apt/lists/* \
        && wget --progress=dot:mega https://github.com/hadolint/hadolint/releases/download/v2.6.0/hadolint-Linux-x86_64 \
        -O /usr/bin/hadolint \
        && chmod 755 /usr/bin/hadolint \
        && wget --progress=dot:mega https://github.com/koalaman/shellcheck/releases/download/v0.7.2/shellcheck-v0.7.2.linux.x86_64.tar.xz \
        && tar xvf shellcheck-v0.7.2.linux.x86_64.tar.xz \
        && cp shellcheck-v0.7.2/shellcheck /usr/bin/ \
        && chmod 755 /usr/bin/shellcheck \
        && wget --progress=dot:mega https://github.com/terraform-docs/terraform-docs/releases/download/v0.16.0/terraform-docs-v0.16.0-linux-amd64.tar.gz \
        && tar xvf terraform-docs-v0.16.0-linux-amd64.tar.gz \
        && mv terraform-docs /usr/bin/ \
        && chmod 755 /usr/bin/terraform-docs

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1