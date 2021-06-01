# django-rpi-tph-docs
Documents for my django-rpi-tph-monitor project.

# English document(default)

## repository

- HTTPS:
  - https://github.com/mitsuhisaT/django-rpi-tph-docs.git
- SSH
  - git@github.com:mitsuhisaT/django-rpi-tph-docs.git

## branch

```shell
$ git checkout i10n/en
```

## Another languages

For example Japanese.

Checkout another language branch.

```shell
$ git checkout i10n/ja
```

If first time, you must create branch and new repository(project).

```shell
$ git checkout -b i10n/{language code} --track remote/i10n/{language code}
```

Please read 
[Internationalization](https://www.sphinx-doc.org/en/master/usage/advanced/intl.html).

Generate po files.

```shell
$ sphinx-intl update -p _build/gettext -l ja
```

Commit and Push po files.

```shell
$ git commit -m "docs: because update and add some describes."
$ git push
```

TODO describe merge to develop branch.

Last, change default branch `i10n/en`.

```shell
$ git checkout i10n/en
```

# Another language document

For example Japanese.

## Clone repository

```shell
$ git clone git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git
```

Change repository directory.

```shell
$ cd django-rpi-tph-docs-l10n-ja
```

## Set up for Sync main repository

```shell
$ git remote -v
origin	git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git (fetch)
origin	git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git (push)
```

Add [upstream](https://github.com/mitsuhisaT/django-rpi-tph-docs).

```shell
$ git remote add upstream git@github.com:mitsuhisaT/django-rpi-tph-docs.git
$ git remote -v
origin	git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git (fetch)
origin	git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git (push)
upstream	git@github.com:mitsuhisaT/django-rpi-tph-docs.git (fetch)
upstream	git@github.com:mitsuhisaT/django-rpi-tph-docs.git (push)
```

Syncronize upstream, document main repository.

```shell
$ git fetch upstream
From github.com:mitsuhisaT/django-rpi-tph-docs
 * [new branch]      develop    -> upstream/develop
 * [new branch]      i10n/en    -> upstream/i10n/en
 * [new branch]      i10n/ja    -> upstream/i10n/ja
 * [new branch]      main       -> upstream/main
```

```shell
$ git branch --all
* i10n/ja
  remotes/origin/HEAD -> origin/i10n/ja
  remotes/origin/develop
  remotes/origin/i10n/en
  remotes/origin/i10n/ja
  remotes/origin/main
  remotes/upstream/develop
  remotes/upstream/i10n/en
  remotes/upstream/i10n/ja
  remotes/upstream/main
$ git merge upstream/i10n/ja
Already up to date.
$ git push
Everything up-to-date
```

You can edit po files in `locale/{language code}/LC_MESSAGES` for translate Japanese.

After translate, you must commit, push and pull request.