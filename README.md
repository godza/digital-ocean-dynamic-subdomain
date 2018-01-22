# Digital Ocean Dynamic Subdomain

Getting tired of dyndns and no-ip services ripping you off with high prices of their service? Do you have DigitalOcean dropplet and manage your dns via their service?
Well you're in luck.

This script uses DigitalOcean API to update subdomains of domains you manage using their service and updates them with public IP address of server/computer/device you run this script on.

That way you get subdomain that will point to the IP address of your modem router. You'll still need to setup port forwarding, NAT translation or setup DMZ to the server you wish to handle requests to your domain, but this way you'll have access to your mediacenter/home server/backup server from anywhere in the world for free.

## Requirements
This script is dependent on `php` binary which you need to install on your server. Read the setup instructions for your operating system to learn how to install it. Some of the operating systems come with `php` pre-installed.

Second requirement is package manager called `composer`. [Visit Composer Website](https://getcomposer.org) to learn how to install it if you haven't already.

## Installation
Choose the folder you wish to install this script in and go to that folder in your terminal.

Clone this repository to that folder with following command:
`git clone https://github.com/godza/digitalocean-dynamic-subdomain.git .`

After that, install necessary packages by running composer with command:
`composer install`

Make sure that our script can be executed by adding x flag to it:
`chmod +x digitalocean-dynamic-subdomain`


## Configuring
Use sample config file to make your own:
`cp config.sample.json config.json`

Edit the `config.json` file and enter your DigitalOcean token you've created in DigitalOcean administration and also enter subdomains and domains you wish to update (you can update multiple domains).

## Runign for the First Time
Execute the script by using `./digitalocean-dynamic-subdomain`.

In few seconds you should see the messages that notify you which domains are updated

## Runing Periodically
You can use any system to run this script periodically, but we recommend using `cron`.

To setup crontab in editor, use `crontab -e` and add the following line to run this script every hour:
`0 * * * * /path/to/script/digitalocean-dynamic-subdomain`

## Plans for the Future
I will add an algorythm to update the subdomain only if ip address on record has changed