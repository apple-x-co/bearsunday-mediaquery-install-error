# bearsunday-mediaquery-install-error

## 現象

BEAR.Sunday をインストールした後に、Ray.MediaQuery をインストールしようとすると `phpdocumentor/reflection-docblock` などの依存関係が解決できずインストールできない。

## 環境

```text
PHP 8.2.5 (cli) (built: Apr 13 2023 18:27:51) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.2.5, Copyright (c) Zend Technologies
    with Zend OPcache v8.2.5, Copyright (c), by Zend Technologies
```

## 手順

```bash
composer create-project -n bear/skeleton app
cd app
composer require ray/media-query
```

## 実行結果

```text
./composer.json has been updated
Running composer update ray/media-query
Loading composer repositories with package information
Updating dependencies
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - ray/media-query[0.7.0, ..., 0.9.0] require ray/aura-sql-module ^1.12.0 -> satisfiable by ray/aura-sql-module[1.12.0, 1.13.0, 1.13.1].
    - ray/media-query[0.4.3, ..., 0.6.0] require ray/aura-sql-module ^1.11 -> satisfiable by ray/aura-sql-module[1.11.0, ..., 1.13.1].
    - ray/media-query[0.1.0, ..., 0.4.2] require aura/sql ^3.0 -> found aura/sql[3.0.0, 3.1.0] but the package is fixed to 5.0.2 (lock file version) by a partial update and that version does not match. Make sure you list it as an argument for the update command.
    - ray/aura-sql-module[1.11.0, ..., 1.13.1] require psr/log ^1.1 -> found psr/log[1.1.0, ..., 1.1.4] but the package is fixed to 3.0.0 (lock file version) by a partial update and that version does not match. Make sure you list it as an argument for the update command.
    - ray/media-query[0.10.0, ..., 0.11.0] require phpdocumentor/reflection-docblock ^5.3 -> found phpdocumentor/reflection-docblock[5.3.0] but the package is fixed to 5.2.0 (lock file version) by a partial update and that version does not match. Make sure you list it as an argument for the update command.
    - Root composer.json requires ray/media-query * -> satisfiable by ray/media-query[0.1.0, ..., 0.11.0].

Use the option --with-all-dependencies (-W) to allow upgrades, downgrades and removals for packages currently locked to specific versions.
You can also try re-running composer require with an explicit version constraint, e.g. "composer require ray/media-query:*" to figure out if any version is installable, or "composer require ray/media-query:^2.1" if you know which you need.

Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## 表示された解決方法

```bash
composer require ray/media-query -W
```

この方法だと `0.9.0` がインストールされる。現時点の最新版（`0.11.0`）が使えない。
