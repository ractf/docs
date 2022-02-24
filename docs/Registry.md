# RACTF Container Registry

Managed RACTF instances use Amazon [Elastic Container Registry](https://aws.amazon.com/ecr/) for hosting containers. This page shows you how to push containers to the registry for your event.

## Requirements

Before starting, please work with your RACTF team to collect the following details:

* Registry URL
* AWS Access Key ID
* AWS Secret Access Key
* RACTF Event Name

You'll also need to install v1 or v2 of the AWS CLI, documentation on that can be found [here](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html). In the event that you need to change your AWS credentials, please reach out to your RACTF team as soon as possible.

## Steps

The steps below are for `docker`, but you can substitute this for `podman` without issues. You should also be able to use either container engine on Windows, but the recommended environment is Linux.

To update a container, push a new container with the same tag and your update will be automatically deployed.

1. Login to AWS.

   ```shell
   $ aws configure --profile ractf
   AWS Access Key ID [None]: AAAA...
   AWS Secret Access Key [None]: AAAA....
   Default region name [None]: eu-west-2
   Default output format [None]:
   ```

2. Configure your Docker client credentials. These credentials will expire after 12 hours, at which point you will need to run this command again.

   ```bash
   aws ecr get-login-password --region eu-west-2 --profile ractf | docker login --username AWS --password-stdin <Registry URL>
   ```

3. Create a container with the right tag.

   1. To tag an existing container

      ```bash
      docker tag <Existing Tag> <Registry URL>:<RACTF Event Name>/<Container Name>
      ```

   2. To build a new container.

      ```bash
      docker build -t <Registry URL>:<RACTF Event Name>/<Container Name> .
      ```

4. Push your container.

   ```bash
   docker push <Registry URL>:<RACTF Event Name>/<Container Name>
   ```
