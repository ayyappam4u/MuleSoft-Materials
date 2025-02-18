**Bulk API 2.0:**
The Salesforce Bulk API 2.0 is a REST-based API designed to handle large volumes of data, typically for operations like inserting, updating, upserting, or deleting a large number of records in Salesforce. It allows you to efficiently process thousands to millions of records asynchronously. 
Bulk API 2.0 simplifies uploading large amounts of data by breaking the data into batches automatically. All you have to do is upload a CSV file with your record data.
We can process 100 million records per 24-hour period.
Salesforce creates a separate batch for each 10,000 records in your job data internally.
Key Features of Bulk API 2.0:
Asynchronous Processing: It processes large amounts of data in batches, freeing up your system and Salesforce from waiting on each individual record.
No Need for Complex Setup: Unlike Bulk API 1.0, you don't need to manually define the batch sizes or process them individually. You simply upload the data and let Salesforce handle the rest.
Support for Insert, Update, Upsert, and Delete: Bulk API 2.0 supports all these operations, and you can define what happens when a record already exists (upsert) or when data is inserted or updated.

**Create:**
  Create operation allows you to insert a new record into a Salesforce object (e.g., Account, Contact, Lead).
  The maximum number of records you can insert in a single REST API call is usually limited to 200 records
**Update**:
  The Update operation in Salesforce allows you to modify existing records in Salesforce. You typically use this operation when you have a record that already exists and you want to update some of its fields with new data.
**Upsert**
    The Upsert operation in Salesforce refers to a process where a record is either inserted or updated based on whether it already exists in Salesforce. The            decision is typically made based on a unique field, like an ID or an External ID field.
  
    Insert: If the record does not exist (i.e., the unique field is not found), Salesforce will create a new record.
    Update: If the record already exists (i.e., a match is found based on the unique field), Salesforce will update the existing record with the new values.
**Delete**:
The Delete Operation in Salesforce is used to remove records from Salesforce. When performing the delete operation, the specified record is permanently removed from Salesforce. 

=============================================================================================================================================================
Event-Driven Architecture (EDA) in MuleSoft focuses on the asynchronous, decoupled flow of events between different systems, applications, and services. 
MuleSoft is a popular integration platform that enables the creation and management of APIs, microservices, and event-driven solutions. In the context of MuleSoft, EDA enables the development of reactive, real-time, and loosely coupled integrations.

**Example of Event-Driven Architecture with MuleSoft:**
Let’s take an example where an order management system needs to trigger events when an order is placed, processed, and shipped. This can be implemented in an event-driven architecture as follows:

**Order Placement:**
When a customer places an order, an event is generated (e.g., OrderPlaced event).
The order placement system acts as an event producer that sends the event to an Anypoint MQ queue or a Kafka topic.

**Order Processing:**
A service listening for OrderPlaced events is an event consumer. It subscribes to the queue or topic (using Anypoint MQ Listener or Kafka Listener).
Once the event is received, the service processes the order, such as validating payment or inventory.

**Shipping:**
After processing the order, the order service can trigger another event, e.g., OrderShipped.
Another service (such as the shipping service) can listen to the OrderShipped event and handle the shipping process.

**Benefits of Using EDA in MuleSoft:**
Decoupling: 
Systems are decoupled from each other since they communicate through events rather than direct API calls. This improves flexibility and maintainability.
Asynchronous Processing:
EDA allows asynchronous communication, enabling better scalability and responsiveness, especially when dealing with high-volume systems.
Real-Time Data Processing:
Events are processed as soon as they occur, allowing for real-time processing, such as customer notifications, fraud detection, or inventory updates.
Scalability:
Event-driven systems are naturally more scalable since components can scale independently, and events can be queued and processed at different rates by different consumers.

**Salesforce Streaming Events:**
**Push Topic:** Based on SOQL queries that define which records or fields to monitor for changes (e.g., when a record is created, updated, or deleted).
**Generic Events:** These events will use when we want to send and receive custom notifications.
**Platform Events:** Platform events in Salesforce allow us to define custom events, and you can use these events to trigger workflows or notify systems outside of Salesforce.
**Change Data Capture(CDC) Events:** Provides real-time event notifications about changes in Salesforce records (e.g., creation, update, deletion) for standard and custom objects.


**CDC Events:**

In MuleSoft, the Replay Channel Listener is a component used to handle events that may have been missed or failed to be processed in an event-driven flow. This concept is useful when working with event-driven architectures (EDA), such as Platform Events, Change Data Capture (CDC) events, or Pub/Sub mechanisms (e.g., JMS or Kafka).

When a listener processes events, sometimes the event might not be successfully consumed due to errors, network issues, or other failures. The Replay Channel Listener ensures that failed events can be reprocessed and handled correctly, guaranteeing reliable message delivery.

  >Set up replay mechanisms based on the specific platform (e.g., Replay ID for Salesforce or offset for Kafka).
