# DKR

`dkr` is a simple shell script to easy docker usage by developers

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
