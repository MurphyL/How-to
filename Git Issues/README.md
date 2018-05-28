# `Git`常见问题

## How to fix a corrupt git index

### Message:

```shell
  error: index uses  extension, which we do not understand
  fatal: index file corrupt
```

### Reslove:

```shell
  rm .git/index.lock .git/index
```
