
# cf-macro-latest-layer-version

A CloudFromation Macro that sets the Layer version on a Lambda function to the latest available in the current account. It uses a lambda function with the code embeded in the template. 

## Installation

Install the CloudFormation template into your AWS account. This will create a Lambda function with the name you specified as a parameter in your cloud formation and a runtime of Node.js version 8.10. Using the console, locate the Lambda function and change the runtime version to nodejs10.x (This is required since currenlty CloudFromation template with emebeded code won't support a runtime of nodejs10.x)

## Usage

In your CloudFormation Template that deploys your lambda:
- specify the layer using the layer name or the arn of the layer whitout the version segment
- declare your macro in the Transform section 

## Example

Specify your lambda layer by name:

```yaml
Resources:
  LambdaFunction:
    Type: AWS::Lambda::Function
    Properties:
      Code:......
      Handler: index.handler
      Layers:
        - your-layer 

```
In the Transform section:

```yaml
Transform: name-of-macro-latest-layer-version
```