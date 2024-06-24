# PHP linting scripts & configuration

The files from this repository can be added to any PHP project to setup complete linting.

This repository works well together with [lode/playground](https://github.com/lode/playground).


## Linters

- phpcs
- phpstan
- rector
- swiff-knife
- symfony (container, twig, yaml)


## Setup

To get started clone the repository and copy to your own repository:

- `script/*`
- `phpcs.xml`
- `phpcs.bonus.xml`
- `phpstan.neon`
- `phpstan.bonus.neon`
- `rector.php`
- `.github/workflows/lint.yml`
- the Usage section of this readme to your own documentation, e.g. `script/README.md`

And install composer packages for the linters:

```bash
composer require --dev \
    squizlabs/php_codesniffer \
    phpstan/phpstan \
    phpstan/extension-installer \
    phpstan/phpstan-strict-rules \
    phpstan/phpstan-deprecation-rules \
    rector/rector \
    rector/swiss-knife
```

Optionally you can setup more phpstan extensions:

```bash
composer require --dev \
    phpstan/phpstan-doctrine \
    phpstan/phpstan-phpunit \
    phpstan/phpstan-symfony
```


## Usage

Daily usage to use linters on the current branch's diff:
- `./script/lint`
- `./script/fix`

Run only a single tool (on the current branch's _files_):
- `./script/lint phpstan`
- `./script/fix rector`

Run a single tool for the whole project:
- `./script/lint phpstan --everything`
- `./script/fix rector --everything`

Do better than what's required:
- `./script/lint --bonus`
- `./script/fix --bonus`
- `./script/lint phpstan --bonus`
- `./script/fix rector --bonus`

Get more options:
- `./script/lint --help`
- `./script/fix --help`


## Using with(out) Docker

This repository works well together with the Docker setup from [lode/playground](https://github.com/lode/playground).

If you don't use that repository, and experience issues running the scripts, you can change:

- `./script/lint` to remove the part defining `CONSOLE_PREFIX`
- `./script/fix` to remove the part defining `CONSOLE_PREFIX` and `CONSOLE_PREFIX_WITHOUT_TTY`
- `./script/lint` and `./script/fix` to remove all references of `$CONSOLE_PREFIX ` and `$CONSOLE_PREFIX_WITHOUT_TTY `

Alternatively, or if you run another Docker setup, you can adjust the parts defining the console-prefix to work with your Docker setup.


## To Do

- Use `linting.env` file for configuration
- Setup as composer package
