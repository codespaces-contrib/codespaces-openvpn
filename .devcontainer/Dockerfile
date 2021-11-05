# You can use any debian based image you want
FROM mcr.microsoft.com/vscode/devcontainers/base:0-bullseye

# Install openvpn client
RUN export DEBIAN_FRONTEND=noninteractive && apt-get update \
    && apt-get -y install --no-install-recommends openvpn \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/library-scripts \
    #
    # Remove the OPENVPN_CONFIG variable since we don't neeed it after is written to a file 
    && echo "unset OPENVPN_CONFIG" | tee -a /etc/bash.bashrc > /etc/profile.d/unset-openvpn-config.sh \
    && if [ -d "/etc/zsh" ]; then echo "unset OPENVPN_CONFIG" >> /etc/zsh/zshenv; fi
