# udacity-cloud-devops-project-2

This is a task to deploy an AWS infrastructure with CloudFormation. The detailed requirement is showned in [project-portfolio diagram](./project-portfolio.png).

## Build

The script can be reused to build the entire infrastructure including the network and servers.

```
# first deploy network stack
./create.sh my-network-stack my-network.yml my-network-parameters.json

# then deploy servers stack
./create.sh my-servers-stack my-servers.yml my-servers-parameters.json
```

## Note
- in the UserData of EC2 LaunchConfiguration, apache server might not be started successfully due to lack of config file.
  - run `sudo dpkg --configure -a` could solve this, but needed manual interaction to confirm update.
  - this might be caused by using t2.micro. (the task asked for an instance type better than t3.small, I just used t2.micro for debugging purpose.)

- Inside the EC2 instance, the /var/www/html created needs sudo to be changed, like adding files.

