FROM jupyterhub/jupyterhub:5

# Install GitHub OAuth, DockerSpawner, and Docker Engine SDK
RUN pip install --no-cache-dir \
    oauthenticator==16.* \
    dockerspawner>=13 \
    docker>=6.1

# Copy Hub configuration and optional allowed users seed file
COPY jupyterhub_config.py /srv/jupyterhub/jupyterhub_config.py
COPY allowed_users.txt /srv/jupyterhub/allowed_users.txt

WORKDIR /srv/jupyterhub
