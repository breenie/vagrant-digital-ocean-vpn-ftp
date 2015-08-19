# Create a VPN/FTP box on DigitalOcean using vagrant

## Environment variables

You need a DigitalOcean API token and the name of an SSH key.

```sh
export TOKEN={DigitalOcean API token}
export SSH_KEY_NAME={DigitalOcean SSH key name}
```

## Install the Digital Ocean Vagrant Provider

Install the provider plugin using the Vagrant command-line interface:

```sh
vagrant plugin install vagrant-digitalocean
```

## Copy the dist FTP watch upload script

Copy `ftp-watch.dist` to `ftp-watch`. This script is copied to the host and executed when a new file is added to the 
ftp directory. The example included emails the image to Flickr using the Mailgun API.

```sh
cp ftp-watch.dist ftp-watch
```

## Start it up!

```sh
vagrant up --provider=digital_ocean
```

## Grab the VPN profiles

The provisioner creates two profiles, one for the camera which is given a static address and one other profile which can
be considered general purpose which shouldn't clobber the static routing.

Download these to your local machine:

```sh
scp root@HOSTNAME:~/webcam.ovpn .
scp root@HOSTNAME:~/client.ovpn .
```

If you require all of the certificates for your particular flavour of router download those too:

```sh
scp root@HOSTNAME:~/ca.crt
scp root@HOSTNAME:~/webcam.crt
scp root@HOSTNAME:~/webcam.key
scp root@HOSTNAME:~/client.crt
scp root@HOSTNAME:~/client.key
```