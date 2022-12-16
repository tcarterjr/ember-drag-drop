FROM mcr.microsoft.com/devcontainers/javascript-node:0-18-bullseye

# # install Chrome for testing
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \ 
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list
RUN apt-get update && apt-get -y install google-chrome-stable

# Install more global node packages
RUN su node -c "npm install --location=global ember-cli"

# tweak chrome to run with --no-sandbox option in container
RUN sed -i 's/"$@"/--no-sandbox "$@"/g' /opt/google/chrome/google-chrome
