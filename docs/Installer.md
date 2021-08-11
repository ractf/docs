# RACTF Installer
The RACTF Installer is the easiest way to setup your own RACTF instance. All you have to do is download it, and run through a few simple prompts to get started.

## Downloading the installer
1. Download the latest release from [Github](https://github.com/ractf/install/releases/latest/). 

## Running the installer

1. To run the installer, it must be made executable. On Linux, you can use this command to make it executable: `chmod +x install`

2. Once you have the installer downloaded, you can run it with `./install` as root.

## Installer Options

This section lists the installer prompts as they appear in the installer.

1. The first thing the installer will prompt is for the **services** you wish to install.
   
   - **Andromeda**: The pod scheduler integrated with RACTF. Selecting this option will install the Andromeda daemon onto your box inside a docker container.

   - **Core**: The backend for RACTF. Selecting this option will install the RACTF Backend and Traefik onto your box inside a docker container.

   - **Shell**: The frontend for RACTF. Selecting this option will download and compile the RACTF Frontend onto your box, then serve it using Caddy and Traefik to your users.

2. **Short name** of your event. This is displayed in the top left corner of the frontend, and is used to derive the internal name of this install.

3. **LetsEncrypt email** for HTTPS certificate provisioning; You should use an email you control. This email is not sent to anyone other than LetsEncrypt.

4. **API Public URL**. In other words, the URL where client computers can access your instance of Core from.

5. **Frontend URL** - visitors will access the RACTF Frontend (Shell) at this URL.

6. Finally, you'll be asked to enter **credentials** for sending emails. Currently we support 
    - AWS
    - Sendgrid
    - SMTP

## Finishing up

After this, the Installer will generate two files: 
- `/opt/ractf/{{InternalName}}/docker-compose.yaml`
- `/etc/systemd/system/ractf_{{InternalName}}.service`

The `InternalName` is the **short name** set in the installer with a few modifications:
- Lowercased
- Spaces replaced with underscores
-  `.` and `/` characters removed

All that is left now is to: 
1. Setup DNS records. 
   - To do this, **set an A record** for the domain to the public IP of the machine you ran the **Install**er on
2. Start the RACTF service using systemctl
   - run the `systemctl enable --now ractf_{{InternalName}}` command

After DNS propagates, you should be able to go to your **frontend url**, and get started!

**Important: The first account created will be automatically set to the admin role.**

Congratulations on your new RACTF instance! :-) 
