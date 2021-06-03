# django-rpi-tph-docs
Documents for my [django-rpi-tph-monitor](https://github.com/mitsuhisaT/django-rpi-tph-monitor) project.

# 英語のドキュメント(デフォルト)

## リポジトリー

- HTTPS:
  - https://github.com/mitsuhisaT/django-rpi-tph-docs.git
- SSH
  - git@github.com:mitsuhisaT/django-rpi-tph-docs.git

## ブランチ

```shell
$ git checkout i10n/en
```

## 別の言語

例えば日本語。

別言語のチェック・アウト

```shell
$ git checkout i10n/ja
```

もし初めてなら、ブランチと新しいリポジトリーを生成しなければならない。

```shell
$ git checkout -b i10n/{language code} --track remote/i10n/{language code}
```

[国際化](https://www.sphinx-doc.org/ja/master/usage/advanced/intl.html).
を読んでください。

po ファイルを作成します。

```shell
$ cd docs
$ make gettext
$ sphinx-intl update -p _build/gettext -l ja
```

Commit and Push po files.
po ファイルを `git commit` し `git push` します。

```shell
$ git add locale/ja/LC_MESSAGES/*.po
$ git commit -m "docs: because update and add some describes."
$ git push
```

## develop へのマージ

```shell
$ git checkout develop
$ git mearge i10n/ja
$ git push
```

Last, change default branch `i10n/en`.

```shell
$ git checkout i10n/en
```

# 別言語のドキュメント

例えば日本語。

## リポジトリーをクローン

```shell
$ git clone git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git
```

リポジトリーのディレクトリに移動。

```shell
$ cd django-rpi-tph-docs-l10n-ja
```

## 主リポジトリーの設定

```shell
$ git remote -v
origin	git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git (fetch)
origin	git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git (push)
```

[upstream](https://github.com/mitsuhisaT/django-rpi-tph-docs) を追加。

```shell
$ git remote add upstream git@github.com:mitsuhisaT/django-rpi-tph-docs.git
$ git remote -v
origin	git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git (fetch)
origin	git@github.com:mitsuhisaT/django-rpi-tph-docs-l10n-ja.git (push)
upstream	git@github.com:mitsuhisaT/django-rpi-tph-docs.git (fetch)
upstream	git@github.com:mitsuhisaT/django-rpi-tph-docs.git (push)
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
```

ドキュメントの主リポジトリーと同期する。

```shell
$ git fetch upstream
From github.com:mitsuhisaT/django-rpi-tph-docs
   18c17fb..537f31c  develop    -> upstream/develop
   18c17fb..dfea83c  i10n/ja    -> upstream/i10n/ja
```

```shell
$ git merge upstream/develop
Updating 18c17fb..537f31c
Fast-forward
 README.md                                    | 13 +++++++++++--
 docs/locale/ja/LC_MESSAGES/gettingstarted.po | 50 ++++++++++++++++++++++++--------------------------
 docs/locale/ja/LC_MESSAGES/index.po          | 20 ++++++++------------
 docs/locale/ja/LC_MESSAGES/prepare.po        |  4 ++--
 docs/requirements.txt                        |  2 +-
 5 files changed, 46 insertions(+), 43 deletions(-)

$ git push

$ git merge upstream/i10n/ja
Already up to date.
$ git push
Everything up-to-date
```

## ブランチを変える

```shell
$ git checkout i10n/{language code}
```

Then, you can edit po files in `locale/{language code}/LC_MESSAGES` for translate Japanese.

After translate, you must commit, push and pull request.