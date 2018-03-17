### [Guidelines](README.md) | [Sample torrent file](https://github.com/stevemclaugh/preservation-torrent/blob/master/DataRefuge_001_test.torrent?raw=true)


# Setup guide: Creating and seeding a torrent on a VPS

Create a new virtual private server. I'm using Ubuntu 16.04 on DigitalOcean, with Docker 17.12.0-ce pre-installed.

> <img src="img/DigitalOcean.png" width="800" />


`ssh` to your new VPS.

```
ssh root@your.ip.address.here
```

Open ports `9091` and `51413` in your firewall and make sure `zip` and `unzip` are installed.

```
ufw allow 9091
ufw allow 51413
apt-get -y install zip unzip
```

Next, download the Docker container we'll be using: my fork of [dperson's container](https://github.com/dperson/transmission) for the open-source BitTorrent client [Transmission](https://transmissionbt.com). I fixed a few bugs and added Transmission's command-line tool for creating new torrents.

```
docker pull stevemclaugh/transmission
```

When it finishes downloading, enter the following command to run the container in detached mode. This will create several new directories in your server's file system under `/home/transmission-daemon/`.

```
docker run --name transmission -it -d -p 51413:51413 -p 51413:51413/udp -p 9091:9091 -v /home/transmission-daemon:/var/lib/transmission-daemon stevemclaugh/transmission
```

`cd` into Transmission's `Downloads` directory.

```
cd /home/transmission-daemon/Downloads
```

Download and unzip our data bundle.

```
wget http://www.stephenmclaughlin.net/Ubu/Ubu-test-001.zip

unzip Ubu-test-001.zip
```

Next we will create a list of checksums for each file in the set.

```
find Ubu-test-001/* -type f -exec md5sum {} \;  > Ubu-test-001/_checksums.md5

zip -r Ubu-test-001.zip Ubu-test-001/
```

In the future, you can use the this checksum file to verify that everything has arrived intact. This may take a few minutes.

```
md5sum -c Ubu-test-001/_checksums.md5
```



If every file passes the check, we're ready to create our torrent. Enter the following command to launch a shell session in the running Docker container.


```
docker exec -ti transmission /bin/bash
```

Now `cd` to the `Downloads` directory.

```
cd /var/lib/transmission-daemon/Downloads
```

The following command creates a torrent file for the directory `Ubu-test-001/`, which is saved to `transmission-daemon/info/torrents/Ubu-test-001.torrent`.

```
transmission-create -n Ubu-test-001/ \
--tracker udp://tracker.opentrackr.org:1337 \
--tracker http://tracker2.wasabii.com.tw:6969/announce \
-o ../info/torrents/Ubu-test-001.torrent
```

Now we'll return to Ubuntu. To close your session in the Docker container, press `ctrl+p`, then `ctrl+q`.

Enter the following two commands to kill the running Docker container and restart it in detached mode.

```
docker rm -f transmission
docker run --name transmission -it -d -p 51413:51413 -p 51413:51413/udp -p 9091:9091 -v /home/transmission-daemon:/var/lib/transmission-daemon stevemclaugh/transmission
```

In your browser, navigate to `your.ip.address.here:9091`. The default username and password are 'admin' and 'admin'. (You can change them by editing `/home/transmission-daemon/info/settings.json`.)

> <img src="img/Transmission.png" width="800" />

Once Transmission finishes verifying your data, it will seed the files for anyone who opens the torrent file we just created at `/home/transmission-daemon/info/torrents/DataRefuge_001_test.torrent`. Download that file using an FTP client and distribute widely.



&nbsp;

<p xmlns:dct="http://purl.org/dc/terms/" xmlns:vcard="http://www.w3.org/2001/vcard-rdf/3.0#">
  <a rel="license"
     href="http://creativecommons.org/publicdomain/zero/1.0/">
    <img src="http://i.creativecommons.org/p/zero/1.0/88x31.png" style="border-style: none;" alt="CC0" />
  </a>
</p>
