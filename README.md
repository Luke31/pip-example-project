# Pip example project

Project to showcase installing of python dependencies using github Actions from private git reporistories.
Python libary to install: [aws-pylib](https://github.com/Luke31/aws-pylib) (fork)

## git ssh with key-pair
1. Create a keypair somewhere using `ssh-keygen -t rsa -b 4096` without passphrase. Don't overwrite your current one ;)
1. Add a new Deploy key to `aws-pylib` with the content of file `id_rsa.pub`
1. Add a new secret to this dependent project `pip-example-project`
    `ACTIONS_PIP_ACCESS_EXAMPLE_PROJECT_PRIV` = content of `id_rsa`
1. Commit a change and see how the github actions `install-dep-ssh` is running

## git https with PAT (Personal access token)
1. Generate [Personal access tokens](https://github.com/settings/tokens)
    `ACTIONS_PIP_ACCESS_EXAMPLE_PROJECT_TOKEN`
    If you don't want to create the token on a real user, create a [machine user git account](https://developer.github.com/v3/guides/managing-deploy-keys/#machine-users).
1. Add a new secret to this dependent project `pip-example-project` with same name:
    `ACTIONS_PIP_ACCESS_EXAMPLE_PROJECT_TOKEN` = generated token
1. Commit a change and see how the github actions `install-dep-https` is running
