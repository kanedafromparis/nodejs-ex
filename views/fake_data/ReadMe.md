
# Padded image folder

This folder is create in order to have a large size folder of images for a test

It is created thanks to http://lorempixel.com/ web site

```bash
for i in {1..50}; do 
    SLEEP=$(( $RANDOM % 5 + 1 ));
    FILESIZE=$(( $RANDOM % 50 * 100 ));
    SUBFOLDER=$(( $RANDOM % 1000 + 1 ));
    WIDTH=$(( $RANDOM % 500 + 1 ));
    HEIGHT=$(( $RANDOM % 500 + 1 ));
    mkdir -p $SUBFOLDER;
    curl -q http://lorempixel.com/g/$WIDTH/$HEIGHT/  > ./$SUBFOLDER/`date +%y%m%d%H%M%S`-$i.png;
    dd if=/dev/urandom of=./$SUBFOLDER/`date +%y%m%d%H%M%S`-$i.bs bs=1024 count=$FILESIZE;
    sleep $SLEEP;
    du -sh .;
done
```
