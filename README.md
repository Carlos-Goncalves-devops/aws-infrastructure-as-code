# aws-infrastructure-as-code
Deploy high-availability web app using CloudFormation

#### diagram.jpeg
visual representation of cloudformation

#### servers.yml
For servers.yml to create Bastion resource you need to create a valid key pair. Go to EC2 Dashboard and in Key Pairs section under Network & Security, create a key pair with name UdacityProjectKeyPair with .pem extention.

If you do not want to use Bastion Host remove BastionSecurityGroup and BastionHost in resources and remove BastionKeyPairName from parameters in server.yml and server-parameters.json. 

#### server-parameters.json
The JSON file contains:
    "ParameterKeys":
         "EnvironmentName"
         "BastionKeyPairName"
    "ParameterValues":
         "UdacityProject"
         "UdacityProjectKeyPair"

#### command to create the stack
run aws cloudformation create-stack --stack-name $1 --template-body file://$2  --parameters file://$3 --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=$4

#### command to update the stack
aws cloudformation update-stack --stack-name $1 --template-body file://$2  --parameters file://$3 --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=$4

#### command to validate template
aws cloudformation validate-template --template-body file://path.yml
