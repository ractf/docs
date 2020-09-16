# The RACTF Installer
The RACTF Installer is currently the easiest way to setup your very own RACTF instance. Just download, run through a few simple prompts and get started! Let's take a closer look.

## Obtaining the installer
The easiest way to get the installer is to download the latest release from the github page [here](https://github.com/ractf/install/releases/latest/). Once you've downloaded it, you can run it as root with `sudo ./install`. (If you get a permissions error, you may have to make the binary file executable. To do so on UNIX systems, you can use the command `chmod +x install`)

## The installer prompts: A detailed guide
The first thing the installer will prompt you for is to select which services you wish to install. The descriptions of the services are as follows:
 - Andromeda: The pod scheduler integrated with RACTF. Selecting this option will install the Andromeda daemon onto your box inside a docker container.
 - Core: The backend for RACTF. Selecting this option will install the RACTF Backend and Traefik onto your box inside a docker container.
 - Shell: The frontend for RACTF. Selecting this option will download and compile the RACTF Frontend onto your box, then serve it using Caddy and Traefik to your users.

The next thing the installer will prompt you for is the "short name" of your event. This is displayed in the top left corner of the frontend and is used to derive the internal name of this install.

The next thing you'll be asked for is an email to send to LetsEncrypt for HTTPS certificate provisioning. Use an email you control. This email is not sent to anyone other than LetsEncrypt.

The next thing you'll be asked for is the public URL of your API. In other words, the URL where client computers can access your instance of Core from.

After this, you'll be asked for the URL visitors will access your site through. This is where your users will access your instance of Shell.

Finally, you'll be asked for a pair of AWS keys for mail.

## Finishing up

After this, the Installer will generate two files: `/opt/ractf/{{InternalName}}/docker-compose.yaml` and `/etc/systemd/system/ractf_{{InternalName}}.service`. The `InternalName` is whatever you specified as the event name, sent to lower case, with spaces replaced with underscores and `.` and `/` characters removed.

All you need to do now is point the DNS at the requisite boxes (Point an A record for the domain to the public IP of the box you just ran Install on), and `systemctl enable --now ractf_{{InternalName}}` to start the RACTF service for all the components you installed on that box. After DNS propogates, you should be able to go to whatever you set the frontend domain to, and get started! Congratulations on your new RACTF instance!
