# Cewl

## To spider a site and write all found words to a file
```shell
cewl -w <file> <url>
```

## To spider a site and follow links to other sites
```shell
cewl -o <url>
```

## To spider a site using a given user-agent 
```shell
cewl -u <user-agent> <url>
```

## To spider a site for a given depth and minimum word length
```shell
cewl -d <depth> -m <min word length> <url>
```

## To spider a site and include a count for each word
```shell
cewl -c <url>
```

## To spider a site inluding meta data and separate the meta_data words
```shell
cewl -a -meta_file <file> <url>
```

## To spider a site and store email adresses in a separate file
```shell
cewl -e -email_file <file> <url>
```
