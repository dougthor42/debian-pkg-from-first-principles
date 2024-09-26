Create the deb package:

First, make sure you're in this directory.

Then make the control tar file:

```
# long form
tar \
    --create \
    --file control.tar \
    --owner=root \
    --group=root \
    --directory=control \
    control
# short form
tar -cf control.tar --owner=root --group=root -C control control
```

Then make the data tar file:

```
# long form
tar \
    --create \
    --file data.tar \
    --owner=root \
    --group=root \
    --directory=data \
    opt/
# short form
tar -cf data.tar --owner=root --group=root -C data opt
```

Finally make the deb file:

```
ar \
    r dougthor42-simple_0.0.1-1_all.deb \
    debian-binary \
    control.tar \
    data.tar
```

Install:

```
sudo dpkg --install dougthor42-simple_0.0.1-1_all.deb
```

Verify:

```
tree /opt/basic-pkg/simple
cat /opt/basic-pkg/simple/somefile.txt
```

Uninstall:

```
sudo dpkg --remove dougthor42-simple
```
