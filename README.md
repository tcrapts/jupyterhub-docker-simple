# Jupyterhub
This is a customization of the [jupyterhub-deploy-docker](https://github.com/jupyterhub/jupyterhub-deploy-docker) project. The following modifications have been made:

* `jupyterhub_config.py`: SSL disabled at TLS config. Jupyterhub will be available at port `8000`.
* `Makefile`: everything related to oauth, SSL certificates disabled.
* `Dockerfile.jupyterhub`: install DummyAuthenticator, remove copying of TLS/SSL certificates
* Authenticator: DummyAuthenticator with fixed password is used.
* Jupyterhub Docker image has been adjusted in `singleuser/Dockerfile`.

## Getting started
1. Adjust `userlist` file as needed. Use `admin` as a suffix to specify the user as an admin.
2. Adjust the DUMMY_PASSWORD in `.env` to your preferred password
3. Run `make build`
4. Run `docker-compose up`