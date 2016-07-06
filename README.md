# elastic-beanstalk-slack-notif

A simple node.js script for AWS Lambda to handle SNS notifications.

## Installation
1. Create a new function in Lambda.
2. Paste code in beanstalk-slack-notification.js into code area.
3. Create new role or use existing role for basic execution.
4. Test the Lambda function:
```{
  "Records": [
    {
      "EventSource": "aws:sns",
      "EventVersion": "1.0",
      "EventSubscriptionArn": "arn:aws:sns:us-east-1...ElasticBeanstalkNotifications-Environment-foo-app...",
      "Sns": {
        "Type": "Notification",
        "MessageId": "111",
        "TopicArn": "arn:aws:sns:us-east-1...ElasticBeanstalkNotifications-Environment-foo-app",
        "Subject": "AWS Elastic Beanstalk Notification - New application version was deployed to running EC2 instances",
        "Message": "Timestamp: Thu May 07 23:38:22 UTC 2015\nMessage: Lambda Function Test: New application version was deployed to running EC2 instances.\n\nEnvironment: foo-app\nApplication: FooApp\n\nEnvironment URL: http://foo.com\nRequestId: 222\nNotificationProcessId: 333",
        "Timestamp": "2015-05-07T23:39:18.628Z",
        "SignatureVersion": "1",
        "Signature": "hello-sig",
        "SigningCertUrl": "https://sns.us-east-1.amazonaws.com/...",
        "UnsubscribeUrl": "https://sns.us-east-1.amazonaws.com/...",
        "MessageAttributes": {}
      }
    }
  ]
}
```
5. Hook SNS to Lambda function by subscribing to a topic. Set the protocol to Lambda, endpoint to your function and click 'Create subscription'.
6. Test it out!
