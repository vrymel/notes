# AWS

#### SSH connection to private instances

In order to connect to a private instance, you need to configure SSH agent forwarding.

SSH agent forwarding works by adding the private key (used to connect to instances) from your workstation in `ssh-add`.

    ssh-add -K <path to private key>

Then connect to your bastion host using:

    ssh -A <user@bastion-host-ip>

From the bastion host, you can then SSH to the private instance without providing the private keys.

    ssh <user@private-intance-ip>

Note: If the private instance's private key is different from the bastion host, you need to add both private keys in `ssh-add`.

[Source](https://aws.amazon.com/blogs/security/securely-connect-to-linux-instances-running-in-a-private-amazon-vpc/)