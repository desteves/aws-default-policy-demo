# aws-default-policy-demo


## From scratch

```bash

# create the repo
mkdir aws-default-policy-demo
git init

# policy uses typescript so add ignore modules
echo "**node_modules" >> .gitignore

mkdir infra && cd infra

# use a template
pulumi new container-aws-go 


# check I'm logged into Pulumi Cloud, else run pulumi login
pulumi whoami 

# Update template packages, good practice.
go get -u

# checked I'm logged into AWS
aws sso login --profile work

# re-org repo to prefered way
mv app ../
vi main.go
	#update the app source directory

# Add policy subdir
pulumi policy new aws-cis-compliance-policies-typescript  --dir policypack


# Test everything
AWS_PROFILE=work pulumi up  --policy-pack policypack 

# TA-DA!

```