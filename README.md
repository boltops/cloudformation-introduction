## CloudFormation Tutorial Commands

This is a introduction tutorial that creates a very simple stack so we can focus on learning. It launches 1 single ec2 instance in the us-east-1 region.  You need to have a keypair in that region named 'default'.  The explanation behind the commands are all covered in the tutorial.

Here are the commands listed together for your convenience.

```sh
# template with only an EC2 instance resource
aws cloudformation create-stack --stack-name ec2 --template-body file://ec2.yml

# confirm stack created successfully
aws cloudformation describe-stacks --stack-name ec2

# use a parameter to specify a different instance type
aws cloudformation create-stack --stack-name ec2-$(date +%s) --template-body file://ec2-param.yml --parameters "ParameterKey=InstanceType,ParameterValue=t2.small"

# use a parameters file
aws cloudformation create-stack --stack-name ec2-$(date +%s) --template-body file://ec2-param.yml --parameters file://params.json

# if statement
aws cloudformation create-stack --stack-name ec2-$(date +%s) --template-body file://ec2-if-env-is-prod.yml --parameters "ParameterKey=Env,ParameterValue=prod"

# join function
aws cloudformation create-stack --stack-name ec2-$(date +%s) --template-body file://ec2-join-tag-example.yml --parameters file://params-app-role-env.json
```
