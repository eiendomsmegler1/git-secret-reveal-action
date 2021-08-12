# `git-secret-reveal` GitHub Action

This action

* installs [git-secret](https://git-secret.io/)
* Loads a secret GPG key from input
* Reveal all git-secret files from repository


## Usage

1. Create a GPG key, see [Generating a new GPG key](https://docs.github.com/en/github/authenticating-to-github/managing-commit-signature-verification/generating-a-new-gpg-key)
    * _NOTE Make sure you don't have a passphrase set on the private key_
2. In your repository / organization, create a new secret, go to _Settings > Secrets_ menu. In this example, the secret is called `GPG_SECRET_KEY`
3. In your workflow definition file, add the following steps:

```yaml
# .github/workflows/foobar.yml
  jobs:
    foo:
      ...
      steps:
        - uses: eiendomsmegler1/git-secret-reveal@v0.0.1
          with:
            gpg_key: ${{ secrets.GPG_SECRET_KEY }}
        ...

```