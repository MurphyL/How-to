# `Git`常见问题

## Generating a new SSH key

```shell
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

## How to fix a corrupt git index

### Message:

```shell
  error: index uses  extension, which we do not understand
  fatal: index file corrupt
```

### Reslove:

```shell
  rm .git/index.lock .git/index
  git reset
```
