# Jupyterhub
This is a customization of the [jupyterhub-deploy-docker](https://github.com/jupyterhub/jupyterhub-deploy-docker) project. The goal is to make the deployment as simple as possible. Therefore:
* Jupyterhub is deployed without SSL and must be used behind a proxy (for example nginx or Caddy).
* The password for all user accounts is the same

## Getting started
1. Run `make build`
2. Run `docker-compose up`
3. Jupyterhub is now available at `localhost:8100`. The username is listed in `userlist` and the password can be found in `.env` (key: `DUMMY_PASSWORD`).

## Configuration
* Adjust `userlist` file as needed. Use `admin` as a suffix to specify the user as an admin.
* The Docker image used for Jupyter can configured at `singleuser/Dockerfile`.
* Refer to the [original project](https://github.com/jupyterhub/jupyterhub-deploy-docker) for details about using other authentication methods or SSL configuration.

## Modifications:
* `jupyterhub_config.py`: SSL disabled at TLS config. Jupyterhub will be available at port `8000`.
* `Makefile`: everything related to oauth, SSL certificates disabled.
* `Dockerfile.jupyterhub`: install DummyAuthenticator, remove copying of TLS/SSL certificates
* Authenticator: DummyAuthenticator with fixed password is used.