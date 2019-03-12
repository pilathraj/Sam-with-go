## SAM With Golang

### Pre-Installation

1. [Install the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-windows.html#install-msi-on-windows)
2. [Install SAM Local](https://aws.amazon.com/serverless/sam/)
3. [Install Docker](https://docs.docker.com/install/)
4. [Install Make](http://gnuwin32.sourceforge.net/packages/make.htm)
5. [Install Git](https://git-scm.com/download/win)

## Configure Your AWS account

```bash
cmd > aws configure
```
  It will be asking you to configure AWS Access Key ID,  AWS Secret Access Key, Default region name and Default output format.
  You can find your Access Key ID,  AWS Secret Access Key on  https://console.aws.amazon.com/iam/home?region=ap-south-1#/security_credentials  > Aceess Keys > Create New Access Key.

## Dev
1. Download the files.
git clone https://github.com/pilathraj/Sam-with-go
2. Go to your directory
```bash
cmd > make local
```
3. Deploy insto AWS
```bash
cmd > make deploy
```
