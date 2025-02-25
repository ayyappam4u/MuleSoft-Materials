AWS Simple Notification Service (SNS):
This managed AWS resource is central to the idea of a pub/sub model, wherein a publisher can publish messages to topics with subscribers being subscribed to those topics.
In the event of a message being received on such a topic, all the subscribers of that topic will get notified.
These subscribers can be as varied and as vast as your imagination might extend, starting right from Amazon Kinesis Data Firehose delivery streams to Lambda functions, Amazon SQS queues to HTTP/S endpoints, and AWS Event Fork Pipelines.
Published messages are stored across multiple, geographically separated servers and data centers, so your data is safe and durable.

AWS Simple Queuing Service (SQS):
This secure, durable, and available hosted queue lets us integrate and decouple distributed software systems and components.
SQS allows greater control on what can be done with a message, including robust capabilities like visibility timeouts, delay queues and dead letter queues.
SQS uses redundant infrastructure to provide highly-concurrent access to messages and high availability for producing and consuming messages.
Choose to transmit sensitive data by protecting the contents of messages in queues by using default Amazon SQS managed server-side encryption (SSE), or by using custom SSE keys managed in AWS Key Management Service (AWS KMS)

Simple:
  ![image](https://github.com/user-attachments/assets/0b648556-125b-4acf-8efb-6d296e8e67d7)

  ![image](https://github.com/user-attachments/assets/0f7f1e7c-e125-4a55-8e21-f7d685ff273e)

  ![image](https://github.com/user-attachments/assets/fa18328c-b13e-4f15-967b-5eaa322af13b)


