# Use AWS Trainium to optimize Deep Learning training on ECS

This work demonstrates how to deploy Trainium instances on ECS Cluster with all mandatory requirements to run AWS Neuron SDK and ready for training a Machine Learning model.


## Getting started

There are two alternative files:

- [cloudformation-trainium-ecs.json](https://github.com/aws-samples/ecs-trainium-examples/blob/main/cloudformation/cloudformation-trainium-ecs.json): has a custom userdata script to install AWS Neuron SDK dependencies.

- [cloudformation-trainium-ecs-dlami.json](https://github.com/aws-samples/ecs-trainium-examples/blob/main/cloudformation/cloudformation-trainium-ecs-dlami.json): only set Deep Learning AMI ID, which already has AWS Neuron SDK installed.

Use this CloudFormation file to automatically create all the necessary resources to deploy a ECS enviroment with AWS Trainium.

This files includes:
- 2 public subnets
- 2 private subnets
- Application Load Balancer
- Security Group
- Autoscaling Group
- EC2 instance trn1.2xlarge
- ECS AMI ID
- ECS Cluster


## License
This library is licensed under the MIT-0. For more details, please take a look at the [LICENSE](LICENSE) file.
