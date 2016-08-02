# bash-aliases
List of handy bash aliases

## Docker cleanup

Docker volume cleanup
```
alias dockerclean="docker volume rm \$(docker volume ls -qf dangling=true)"
```

## Dockerized Composer

Using docker inside container to avoid package issues.

```bash
alias composer-data="docker run --name composer-data -v /composer --entrypoint sh composer/composer:php5-alpine"
alias composer-term="docker run --rm -ti -v \$(pwd):/app --volumes-from composer-data --entrypoint sh composer/composer:php5-alpine"
alias composer="docker run --rm -ti -v \$(pwd):/app --volumes-from composer-data composer/composer:php5-alpine"
```

Some laravel commands that integrate with the composer commands:
```bash
alias laravel-installer="docker run --rm -ti --volumes-from composer-data composer/composer:php5-alpine global require \"laravel/installer\""
alias laravel="docker run --rm -ti -v \$(pwd):/app --volumes-from composer-data --entrypoint laravel composer/composer:php5-alpine"
```

## Git shortcuts

```bash
alias gits="git status"
alias gcm="git commit -m"
alias gcam="git commit -am"
alias gck="git checkout"
alias glog="git log --all --graph --decorate --oneline"
alias glogbis="git log --all --graph --decorate --oneline --simplify-by-decoration"
```
