CloudHub 2.0 is a fully managed, containerized integration platform as a service (iPaaS) where you can deploy APIs and integrations as lightweight containers in the cloud.
Isolation of application in Cloudhub2.0.
CloudHub 2.0 is a multi-tenant environment (allowing multiple customers to share resources), the platform ensures that each customer’s applications and data are securely isolated 
ensuring that one tenant’s application cannot interfere with the operations or data of another tenant.

Key Benefits of CloudHub 2.0:
  >  Container based model(as opposed to vm based deployment in CH 1.0) so it enable applications spin up much faster. So application deployed and application become up and running the toatl time duration is much 
  lesser than CH1.0
  >  vCore allocation is possible with more granularity than CH1.0. In CH1.0, we can allocate 0.1, 0.2 then staright away to 1 vcore, 2. But in CH2.0, point to 0.1, 0.2, 0.5, 1, 1.5,2,2.5 
  >  Outbound firewall rule configuration to control egress traffic
  >  Application clustering on more than  one replica seamlessly. Deployed application to CH2.0 by selecting more than one replica than this clustering option will be available automatically
  >  Zero infrasrtucture maintenance and advnace set up is required for application deployment in shared space.

Where CH2 is better than CH1?
  .  Newly added fractional vCore- reduces the complexity of resource management. Instaed of going straight away to 2.0 there will be an option to select 1.5. So Resouce optimization become flexible.
  .  Autoscaling of Private ingress load balancer. In CH1.0, we configured dedicated load balancer with minimum 2 worker then if need to scale up then we need to add worker manually for DLB.
  .  VPN High Availabily by default
  .  Application deployed on Private spaces have both private and public end points by default.
  .  Configuring multiple public end points for one application is also possible in private space.
  .  Log enable/disable feature is by default.
  .  Application names need not be globally unique in ch2- it will append 6 digit unique id automatically and there shard id which is specific private space so every private space have another unique ID and that 
      will be managed by CH2.0 internally. 
        example: myapp-uniqId.shard.usa-e1.cloudhub.io
          myapp: Application name
          uniqId: A 6-digit value appended to the app name to ensure uniqueness
          shard: A 6-digit value associated with the space (private or shared) that the app is deployed to.
          usa-e1: region deployed application
  .  It possible to edit or update TLS context in CH2.0

Key Considerations:
  1.  Does not support direct connect and VPC peering for extending with external networks CH2.0 will support only VPN Network and trasient Gateway.
  2.  Application deployed in CH2.0 if they are not running it will consume vcore. In CH1, if we stopped the application then vcores released we can use it for other applications but in cloudhub 2.0 if we stopped
       application also it will consume the assigned vcores it will not release those vcores. If we want to get back these v cores then we need to delete application to free up space.
  3. Redployment is the only option to move the applicationsbetween regions. If we want to move the application from usa-e1 to usa-e2 then we need to deploy the application from souce code to target regiona and
     then we can delete the application in source region.
  4. Private spaces can be associated with multiple environments based on the type of environments and Business Groups.
  5. CH2.0 only supports 4.3.0 and higher versions.
  6. Both HTTP and HTTPS traffic uses 8081 port where as in CH1.0 Http ports are associated with 8081 and HTTPS with 8082
  7. Application bursting depends on the resource usage of other applications that are deployed in the same private sapce and not guaranteed.

CloudHub 2.0 does not support the following application features or functions that CloudHub 1.0 supports:

  Mule versions prior to 4.3.0
  Overwriting JVM parameters
  Overriding default JVM truststores with custom truststores
  Creating custom notifications
  Using the CloudHub Connector
  TLS 1.0. Use 1.2 or 1.3 instead

Shared Space:
  A shared space is an elastic cloud of resources that includes Mule instances running in a multi-tenant environment. 
  CloudHub 2.0 provides one shared space in each supported region, to which you deploy your integration applications.
  Deploying to a shared space requires no setup or maintenance of the underlying infrastructure.

  You can deploy apps to the shared space in a region if:
    You don’t require isolation from the public cloud.
    Your apps don’t need to connect to an on-premises data center.
    Your apps can use the cloudhub.io domain name (rather than a vanity domain name).
    You don’t need to configure custom certificates.
  
  Any of the following features and functionality requires a private space:
    Single-tenancy for your apps
    Network connection (VPN or transit gateway attachment) to a data center
    Vanity domain names
    Custom certificates
    Private endpoints
    Static application source IP addresses

Private Spaces:
  A private space is a virtual, private, and isolated logical space in CloudHub 2.0 in which to run your apps. You can create multiple private spaces, either in the same or different regions.
  You connect your private intranet to your private space to function as a single, private network.
In each private space, you define:
  A private network, which is a virtual cloud where apps deployed to this private space run.
  One or more connections from the private network to your external network, either via Anypoint VPN or a transit gateway.
  TLS contexts, which define the domains that are available when deploying apps to the private spaces, and optionally enable mutual TLS.
  Firewall rules to allow and block inbound and outbound traffic to your private space.
  The environments and business groups to allow to deploy to the private space.

**Private Network:**
    When you create the private network, you associate a range of IP addresses for the apps in your private space to use, the region in which they run, and optionally, any internal DNS servers to resolve requests to custom domains.
    You can configure multiple private spaces in a single region, enabling you to set up separate isolated networks for your production and non-production environments, such as dev or staging.
    You can connect a private space to your private network using the following methods:

      1.  Anypoint Virtual Private Network
      2.  Transit Gateway Attachments
**TLS Context**:
  Using Transport Layer Security (TLS) contexts, CloudHub 2.0 enables clients to use custom domains and paths to reach apps deployed to private spaces.
  When setting up a private space, you configure Transport Layer Security (TLS) contexts that define the domains that are available when deploying apps to the private spaces, and optionally enable mutual TLS.
  When deploying an app to the private space, you can use the domains from the TLS contexts to configure multiple endpoints, which clients use to reach the app from the internet. If the domains in the TLS context include a wildcard, you can configure an optional subdomain, such as the app name or an organization. You can create as many endpoints as you need.

Path Rewriting:
  You can configure the app to be accessible from a different path from the base path where the app is listening.

**Firewall Rules**
You control the traffic to and from your private spaces.

**Inbound**
  By default, CloudHub 2.0 allows traffic to the private space on ports 80 (HTTP) and 443 (HTTPS) from anywhere (0.0.0.0/0). Configure firewall rules to allow connections through specified ports, remove ports, or use ports 80 and 443 to control traffic to your private space.
  The private space provides load balancing to balance inbound traffic to apps across multiple replicas.

**Outbound**
  By default, CloudHub 2.0 allows all traffic from the private space to destinations outside the private space. Configure firewall rules to remove this rule and allow traffic only on specified ports.
  By combining firewall rules and TLS context configuration, you can fine-tune the ingress and egress of your application traffic.


**Anypoint Virtual Private Network**
  Anypoint VPN (virtual private network) creates a secure connection between your private space and your on-premises network. Anypoint VPN enables apps running in the private space to access resources in your on-premises data centers behind your corporate firewall.CH2.0 Architecture:

**Transit Gateway Attachments**
  AWS Transit Gateway acts as a cloud router in AWS, simplifying network access between private spaces, on-premises data centers, and third-party software, while providing increased visibility and control over the network. Transit gateways effectively merge your organization’s cloud resources and on-premises datacenters into one network topology.

**CH2.0 Arcitecture:**

![image](https://github.com/user-attachments/assets/9f5e9527-d089-42c9-b5d8-d4f94eb499bb)

CloudHub 2.0 architecture comprises two major components: Anypoint Platform services and shared global regions. 
  1.Integration Applications: Applications that you create and deploy to CloudHub 2.0 to perform integration logic for your business.
                              An integration application is any integration that you’ve built using Anypoint Studio.
  2.Runtime Manager: User interface that enables you to deploy and monitor integrations, and configure your account
  3.Platform Services:Shared CloudHub 2.0 platform services and APIs, which include Anypoint Monitoring, alerting, logging, account management, private spaces/secure data gateway, and load balancing
  4 CloudHub 2.0: An elastic cloud of replicas, Mule instances that run integration applications

![image](https://github.com/user-attachments/assets/e36e48b6-26b7-4465-8752-6f97a6b21cad)

Replicas:
  Replicas are dedicated instances of Mule runtime engine that run your integration applications on CH 2.0.
  Each Replica has minimum of 8GB storage for both system and application. To increase the storage capacity add 2 or more workers.
  If applications need more vcores than available vcores, CH2.0 allows deploy the applications but appllication can not be started to use until additional vcore is added.
  The metaspace limit of application deployed in CH2.0 is 256 MB.
    Metaspace: Metaspace refers to a part of the JVM (Java Virtual Machine) memory where the metadata of the classes and methods used by the application is stored.
  Replicas have the following characteristics:
  Capacity — Each replica has a specific amount of capacity to process data. Select the size of your replicas when configuring an application.
  Isolation — Each replica runs in a separate container from every other application.
  Manageability — Each replica is deployed and monitored independently.
  Locality — Each replica runs in a specific global region, such as the US, EU, or Asia-Pacific.

Multitenancy:
CH 2.0 provides three different levels of multitenancy:

  Shared Global Space:Co-Tenancy without having access to applications and data of other tenant.
  Single-tenant private spaces: They are virtual, private, and isolated space in CloudHub 2.0 for deployment.
  Management console and platform services: They have a shared everything architecture; all tenants share the same web UI, monitoring services, and load balancers.
  
Shared Global Regions:
  CH 2.0 provides the ability to deploy apps in different regions of the world: North America, South America, the European Union, and Asia-Pacific.
  Depending on what region you deploy, the DNS record and the load balancer for your integration might change.
  For example, if you deploy an application named myapp to Canada (Central), the domain used to access the application is myapp-uniq-id.shard.can-c1.cloudhub.io.
  uniq-id: A 6-digit value appended to the app name to ensure uniqueness.
  shard: A 6-digit value associated with the space (private or shared) that the app is deployed to.
  CH2.0 assigns each private space a value for shard. For apps deployed to shared spaces, each region might have multiple shard values. This global distribution enables you to host your integration in the location closest to your services, thus reducing latency.
  The region that you deploy your application to determines the domain provided for your application.
  The load balancer that CH 2.0 uses to route requests resides in the same region as your application.


Availability and Scalability
CloudHub 2.0 is designed to be highly available and scalable through redundancy, intelligent healing, and zero-downtime updates.

Redundant Platform: All CloudHub 2.0 platform services, from load balancing to the API layer, have at least one built-in layer of redundancy and are always available in at least two data centers. All data centers are at least 60 miles apart. This redundancy ensures that even if there is a data center outage, the platform remains available.
Intelligent Healing: CloudHub 2.0 monitors the replicas for problems and provides a self-healing mechanism to recover from them. If the underlying hardware experiences a failure, the platform migrates your application to a new replica automatically.
Zero-Downtime Updates: CloudHub 2.0 supports updating your applications at runtime so end users experience zero downtime. If the application uses the rolling update deployment model, CloudHub 2.0 keeps the old version of your application running while your application update is deploying. Your domain points to the old version of your application until the newly uploaded version is fully started. This allows you to keep servicing requests from your old application while the new version of your application is starting.
Clustering: Clustering provides scalability, workload distribution, and added reliability to applications on CloudHub 2.0. These capabilities are powered by the scalable load-balancing service and replica scaleout features.

Last Mile Security:

  ![image](https://github.com/user-attachments/assets/e31c162a-b169-4250-88c5-6a2ec693f3e9)

  Request is flowing from the outside world or public network or from user to ingress load balancer and then ingres load balancer sending request to mulesoft application.
  So if Mulesoft application listening on HTTP listener then the traffic  supposed to go from Ingress load balancer to application on HTTP.
  If Application is listening on HTTPS listner then the traffic will go to HTTPS since HTTPS is secure transport protocol so that means if the Request is flowing from the outside world the ingress load balancer
  will send the traffic to application on HTTPS so that means it's end-end HTTPS which means this is what we called **last mile security.**
  So this is the last mile between load balancer to application.
  We need to enable the Last Mile Security Option while deploying application listening on HTTPS port.
    ![image](https://github.com/user-attachments/assets/cff94048-7eb3-405e-b861-0aacbb07ae25)


    


  
