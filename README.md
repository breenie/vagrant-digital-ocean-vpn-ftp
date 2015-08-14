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

## Start it up!

```sh
vagrant up --provider=digital_ocean
```