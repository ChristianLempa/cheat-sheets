# wpscan

## basic usage

```shell
wpscan --url "target" --verbose
```

## enumerate vulnerable plugins, users, vulrenable themes, timthumbs

```shell
wpscan --url "target" --enumerate vp,u,vt,tt --follow-redirection --verbose --log target.log
```
