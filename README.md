# DKR

`dkr` is a simple shell script to easy docker usage by developers

## Why use it?

- uses `sudo docker` automaticaly if user is not in docker group
- `dkr b. tag-name` instead of `docker build -t tag-name .`
- `dkr rr tag-name [cmd]` instead of `docker run --rm -it tag-name [cmd]`
- `dkr clean -y`instead of:
    + `docker rmi $(docker images -f "dangling=true" --no-trunc)`
    + `docker rm $(docker ps --filter status=dead --filter status=exited)`
    + `docker volume rm $(docker volume ls -f dangling=true)`

_And I hope that more are comming_

## Dependencies

### To run:

- bash compliant interpreter (bash, zsh)
- sudo (optional, in case user is not in `docker` group)

### To see help (-h option)

As help is inside script, using something like do string, an it's parsed on demand, these are the needed tools to do the magic:

- realpath
- grep
- sed
- awk

## Help from version 0.1.0

```
 v0.1.0

 Usage: dkr command [options]
        -h show dkr help
        --help show docker help

             -h: show help of this script
             -v: show version and exit
              i: alias for docker images
              b: alias for docker build
             b.: build Dockerfile in working folder. Needs image-tag
                                  ($SCRIPT_NAME b. image_name)
             rr: run image with --rm -it
              r: alias for docker run
          clean: clean docker env (usage: $SCRIPT_NAME clean [-y] [c|i|v])
                 <none>     : <none> clear all caches (optional)
                 i          : i clear dangling images
                 c          : c clear exited or dead containers
                 v          : v clear dangling volumes
                 -y         : -y say yes to proceed question (optional)
                                  if only -y, clear all caches without further questions
                                  (must be after clean)
      <unknown>: pass any unrecognized command directly to docker
         <none>: show usage
```
