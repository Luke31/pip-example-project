# Pip example project

Project to showcase installing of python dependencies using github Actions from private git reporistories.
Python library to install: [aws-pylib](https://github.com/Luke31/aws-pylib) (fork)

## git ssh with key-pair
1. Create a keypair somewhere using `ssh-keygen -t rsa -b 4096` without passphrase. Don't overwrite your current one ;)
1. Add a new Deploy key `ACTIONS_PIP_ACCESS_EXAMPLE_PROJECT_PUB` to `aws-pylib` with the content of file `id_rsa.pub`
1. Add a new secret to this dependent project `pip-example-project`
    `ACTIONS_PIP_ACCESS_EXAMPLE_PROJECT_PRIV` = content of `id_rsa`
1. Commit a change and see how the github actions `install-dep-ssh` is running

- Generate new keypair for each dependent application.
- If multiple libraries are required, add content of `id_rsa.pub` as a new deploy key to required repo.
    For this save the `id_rsa.pub` inside the dependent project [id_rsa.pub](https://github.com/Luke31/pip-example-project/blob/master/.github/workflows/id_rsa.pub), so you can easily get the public key to add new deploy keys.

## git https with PAT (Personal access token)
1. Generate [Personal access tokens](https://github.com/settings/tokens) with scope `repo`
    `ACTIONS_PIP_ACCESS_EXAMPLE_PROJECT_TOKEN`
    If you don't want to create the token on a real user, create a [machine user git account](https://developer.github.com/v3/guides/managing-deploy-keys/#machine-users).
1. Add a new secret to this dependent project `pip-example-project` with same name:
    `ACTIONS_PIP_ACCESS_EXAMPLE_PROJECT_TOKEN` = generated token
1. Commit a change and see how the github actions `install-dep-https` is running

- As it is a PAT, dependent project has access to ALL private repositories.