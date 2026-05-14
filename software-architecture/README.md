# What is Software Architecture?

Software architecture is the high-level structure and design of a software system.

It defines:

* How different parts of the system are organized
* How components communicate with each other
* How data flows through the application
* How the system handles scalability, security, performance, and maintenance

Think of it like an architectural blueprint for a building.

* Building architecture → rooms, plumbing, wiring
* Software architecture → services, databases, APIs, servers, communication

---

# Simple Example

For an e-commerce application:

```text id="ibxmb0"
Frontend → Backend API → Database
```

Architecture decides:

* Where frontend runs
* How backend is structured
* How APIs communicate
* Where data is stored
* How scaling works

---

# Main Goals of Software Architecture

* Scalability
* Maintainability
* Performance
* Security
* Reliability
* Flexibility
* Reusability

---

# Common Types of Software Architecture

---

# 1. Monolithic Architecture

All components are combined into a single application and deployed as one unit.

## What It Means

In a monolithic architecture, the entire application is built as a single, tightly integrated codebase. All features—user authentication, payment processing, order management, product catalog—run within the same process and share the same memory space. The application is deployed as a single deployable unit.

## Detailed Explanation

**How It Works:**
- All modules run in a single process
- Direct function/method calls between modules (no network latency)
- Shared database with all tables accessible to all modules
- Single codebase that gets compiled and deployed together

**Example:** A Java Spring Boot e-commerce application where the login service, payment service, order service, and product catalog all run in the same JVM instance.

## Advantages

* **Simple to Develop Initially** - Straightforward setup, no need for inter-service communication protocols
* **Easy Deployment** - Deploy once instead of managing multiple services
* **Good Performance** - No network overhead; direct method calls between components
* **Easier Testing** - Can test the entire application as a single unit
* **Good for Small Projects** - Less infrastructure complexity

## Disadvantages

* **Difficult to Scale** - Must scale the entire application, not individual components
* **Hard to Maintain Large Codebases** - Single codebase becomes massive and difficult to navigate
* **One Bug Can Affect Entire Application** - A memory leak in one module crashes the whole system
* **Technology Lock-in** - Cannot use different technologies for different components
* **Deployment Risk** - Any update requires redeploying the entire application
* **Team Scaling Issues** - Multiple teams working on the same codebase creates conflicts

## When to Use

* Small applications (< 50K lines of code)
* Early-stage startups
* Rapid prototyping and MVPs
* Teams with 1-3 developers
* Applications with simple requirements

## Real-World Examples

* Early versions of Twitter, Facebook (before they scaled)
* Simple CRUD web applications
* Monolithic WordPress installations

---

# 2. Microservices Architecture

Application is divided into small, independent services that communicate over the network, each handling a specific business capability.

## What It Means

Microservices architecture breaks down a monolithic application into small, loosely coupled services. Each service is a separate deployable unit that handles a specific business function. Services communicate with each other via APIs (REST, gRPC) or message queues. Each service can have its own database, technology stack, and deployment schedule.

## Detailed Explanation

**How It Works:**
- Each service is independently deployable
- Services communicate via APIs (HTTP/REST), gRPC, or message brokers (Kafka, RabbitMQ)
- Each service has its own database (polyglot persistence)
- API Gateway routes requests to appropriate services
- Services can be developed in different programming languages
- Each team owns and maintains their service

**Real Example of Communication:**
1. User places order → Order Service receives request
2. Order Service calls Payment Service to process payment
3. Payment Service processes payment and returns result
4. Order Service publishes "OrderCreated" event to message queue
5. Notification Service listens to queue and sends confirmation email

## Advantages

* **Highly Scalable** - Scale only the services that need it (e.g., Payment Service during checkout surge)
* **Independent Deployments** - Deploy Order Service without affecting User Service
* **Easier Maintenance** - Smaller codebases are easier to understand and modify
* **Technology Flexibility** - Use Python for one service, Java for another, Go for another
* **Team Autonomy** - Different teams can work independently without conflicts
* **Fault Isolation** - Failure in Notification Service doesn't crash Order Service
* **Technology Updates** - Update one service's framework without affecting others

## Disadvantages

* **Complex Infrastructure** - Requires container orchestration (Kubernetes), service mesh, monitoring
* **Network Communication Overhead** - Inter-service calls are slower than direct method calls
* **Hard Debugging** - Tracing request flow across multiple services is challenging
* **Distributed Transaction Complexity** - ACID transactions don't work across services
* **Data Consistency Issues** - Ensuring eventual consistency across services is difficult
* **Testing Complexity** - Integration testing across services is more complex
* **Operational Overhead** - More services to monitor, secure, and maintain

## When to Use

* Large-scale applications (> 500K lines of code)
* Team size > 10 developers
* Applications requiring independent scaling
* When different parts need different technologies
* Cloud-native applications
* When you need high availability and fault isolation

## Real-World Examples

* Netflix (uses microservices for thousands of services)
* Amazon (pioneered microservices approach)
* Uber (driver service, rider service, payment service, etc.)
* Spotify (independent artist, track, playlist services)

---

# 3. Layered Architecture (N-Tier)

Application is divided into logical layers where each layer has a specific responsibility. Each layer can only communicate with the layer directly below it.

## What It Means

Layered architecture organizes the application into horizontal layers, each handling specific concerns. Requests flow from the top layer (user interface) down through layers, and responses flow back up. This separation of concerns makes it easy to understand, develop, and test each layer independently.

## Common Layers

The typical four-layer model includes:

## Layer Responsibilities

**Presentation Layer:**
- Handles user interface and user interactions
- Converts user input to business logic requests
- Formats data for display
- Examples: React components, Angular views, JSP pages

**Business Logic Layer:**
- Contains application rules and logic
- Validates data
- Makes business decisions
- Examples: Service classes, domain models, calculations

**Data Access Layer (Persistence Layer):**
- Interacts with the database
- Performs CRUD operations
- Handles database queries and transactions
- Examples: Repository classes, DAOs, ORM configurations

**Database Layer:**
- Stores and retrieves data
- Maintains data integrity
- Examples: MySQL, PostgreSQL, Oracle

## Advantages

* **Organized Structure** - Clear separation of concerns makes code easy to navigate
* **Easy Maintenance** - Changes in one layer don't affect others (mostly)
* **Clear Separation of Concerns** - Each layer has one responsibility
* **Ease of Testing** - Can test each layer independently with mocks
* **Ease of Understanding** - New developers can understand layer responsibilities quickly
* **Reusability** - Business logic layer can be reused by different presentation layers
* **Flexibility** - Can replace one layer without affecting others

## Disadvantages

* **Can Become Tightly Coupled** - Layers often depend on specific implementations
* **Performance Overhead** - Request must pass through multiple layers
* **Large Systems Become Complex** - Not suitable for very large, complex applications
* **Limited Horizontal Scaling** - Difficult to scale individual features independently
* **"Fat Middle Layer"** - Business logic layer tends to grow and become difficult to manage
* **Database Coupling** - Data models often leak into business logic layer

## When to Use

* Enterprise web applications
* Applications with clear separation of concerns
* Teams with multiple skill levels
* Applications requiring extensive testing
* Medium-sized applications (100K - 500K lines of code)
* Traditional business applications

## Real-World Examples

* E-commerce platforms (shopping carts, checkout, inventory)
* Banking systems (account management, transactions)
* HR management systems
* Content management systems
* Project management tools

---

# 4. Client-Server Architecture

A fundamental architecture model where a client makes requests to a server, and the server processes those requests and returns responses. This is one of the most widely used architectures in computing.

## What It Means

In client-server architecture, computation and data are separated between client machines (user devices) and server machines (central computers). Clients are responsible for user interface and user interactions, while servers handle business logic, data storage, and processing. Communication happens over a network (usually HTTP/HTTPS).

## Detailed Explanation

**How It Works:**
1. Client initiates communication by sending an HTTP request
2. Server receives and processes the request
3. Server performs necessary computations and database operations
4. Server sends back a response with data and status code
5. Client receives response and updates the user interface

**Types of Client-Server Architectures:**
- **Thin Client** - Minimal processing on client, server does most work (web apps)
- **Fat Client** - More processing on client, server mainly stores data (desktop apps)
- **Rich Client** - Client has rich UI with significant processing capability (SPAs like React, Vue)

## Advantages

* **Centralized Management** - All data and business logic in one place (easier to secure and update)
* **Easy Updates** - Update server without needing to update all clients
* **Data Security** - Sensitive data stays on server, not distributed
* **Scalability** - Can add more server resources or use load balancing
* **Simple Architecture** - Easy to understand and implement
* **Shared Resources** - All clients access same data source
* **Backup and Recovery** - Centralized backup and disaster recovery

## Disadvantages

* **Server Dependency** - If server goes down, all clients cannot function
* **Server Bottleneck** - Server must handle all clients simultaneously (performance issues at scale)
* **Network Dependency** - Clients must have network connectivity
* **Latency** - Network communication adds delay compared to local processing
* **Scalability Limits** - Single server has capacity limits
* **Single Point of Failure** - One server failure affects all users

## When to Use

* Web applications (most common use case)
* Mobile applications
* Desktop applications connecting to servers
* Multi-user systems requiring centralized data
* Applications requiring data security and consistency
* Collaborative applications (shared documents, etc.)

## Real-World Examples

* **Web Browsers** - Client (browser) requesting web pages from servers
* **Gmail** - Client (browser) communicating with Gmail servers
* **Mobile Banking Apps** - Mobile clients communicating with bank servers
* **Cloud Storage** - Desktop/mobile clients with cloud storage servers (Dropbox, Google Drive)

---

# 5. Event-Driven Architecture

Components communicate through events and messages rather than direct function calls. When something important happens, an event is published to a message broker, and interested components subscribe to those events.

## What It Means

In event-driven architecture, components don't call each other directly. Instead, when an important action occurs (event), a message is published to a central message broker. Other components listening for that event type can react to it asynchronously. This creates loose coupling between services—they don't need to know about each other.

## Types of Event-Driven Architecture

**1. Event Notification:**
- Services only notify other services that something happened
- No data passed, just the event notification
- Receivers fetch data if needed

**2. Event-Carried State Transfer:**
- Event message contains all relevant data
- Receivers have all information without querying
- Reduces need for service-to-service calls

**3. Event Sourcing:**
- All changes are stored as immutable events
- Complete history of all state changes
- Can replay events to reconstruct state

## Technologies

* **Apache Kafka** - Distributed event streaming platform, high throughput, complex
* **RabbitMQ** - Traditional message broker, reliable, widely used
* **AWS EventBridge** - Cloud-native event router
* **Google Cloud Pub/Sub** - Google's pub/sub messaging service
* **Azure Event Hubs** - Microsoft's event streaming service
* **Redis Streams** - Redis-based streaming
* **AWS SQS/SNS** - Simple Queue Service and Simple Notification Service

## Advantages

* **Loose Coupling** - Services don't need to know about each other
* **High Scalability** - Easy to add new event handlers without changing existing services
* **Real-Time Processing** - Immediate reaction to events
* **Asynchronous Communication** - Services don't wait for responses, improving performance
* **Natural Event Expression** - Real-world processes are naturally event-driven
* **Technology Diversity** - Different services can handle events independently
* **Resilience** - If one handler fails, others continue processing
* **Audit Trail** - Complete history of all events that occurred

## Disadvantages

* **Complex Debugging** - Hard to trace request flow across multiple services
* **Event Tracking Difficulty** - Understanding system behavior requires tracking events
* **Eventual Consistency** - Data consistency takes time to propagate
* **Infrastructure Complexity** - Requires sophisticated message broker setup
* **Testing Difficulty** - Asynchronous testing is more complex
* **Message Delivery Guarantees** - Ensuring exactly-once delivery is challenging
* **Learning Curve** - Requires shift in thinking from synchronous to asynchronous

## When to Use

* Real-time systems (fraud detection, stock trading)
* Highly scalable applications
* Systems with complex interactions between components
* Applications requiring audit trails
* Systems needing loose coupling
* IoT applications
* Social media platforms

## Real-World Examples

* **Stock Trading Platforms** - Market data events trigger trading events
* **Fraud Detection Systems** - Transaction events analyzed in real-time
* **Social Media** - User action events (like, comment, share) trigger notifications
* **E-commerce** - Order events trigger payment, inventory, and notification services
* **Streaming Services** - User activity events (watch, pause, resume) for analytics

---

# 6. Service-Oriented Architecture (SOA)

Application is split into reusable, coarse-grained services that communicate through standardized interfaces. SOA is a precursor to microservices with a more enterprise focus.

## What It Means

Service-Oriented Architecture treats an application as a collection of loosely coupled, reusable services that collaborate to fulfill business processes. Unlike microservices, SOA services are larger, often hosted centrally, and communicate primarily through standardized protocols like SOAP and ESB (Enterprise Service Bus). Each service encapsulates business logic and can be reused by multiple applications.

## Key Concepts

**Enterprise Service Bus (ESB):**
- Central mediator for all service communication
- Handles routing, transformation, and orchestration
- Examples: Apache ServiceMix, JBoss Fuse, Oracle ESB

**Service Interfaces:**
- WSDL (Web Service Description Language) based
- SOAP (Simple Object Access Protocol) for communication
- Standardized contracts between services

**Service Repository:**
- Central registry of all available services
- Services register and can be discovered

## Advantages

* **Reusability** - Services can be reused across multiple applications
* **Loose Coupling** - Services interact through well-defined interfaces
* **Standardization** - Using SOAP, WSDL provides standards
* **Legacy System Integration** - Good for integrating older systems
* **Business Alignment** - Services map to business processes
* **Enterprise Support** - Mature tooling and vendor support
* **Governance** - Centralized control through ESB

## Disadvantages

* **ESB Bottleneck** - Central ESB can become a performance bottleneck
* **High Complexity** - ESB setup and configuration is complex
* **Expensive** - Enterprise tools and infrastructure cost more
* **Vendor Lock-in** - Often tied to specific ESB vendors
* **Performance Overhead** - Message transformation and routing adds latency
* **Scalability Issues** - Scaling is limited by ESB capacity
* **Maintenance** - ESB itself becomes complex to maintain

## When to Use

* Large enterprises with multiple existing applications
* Need for legacy system integration
* Standardized service contracts required
* Centralized governance and control needed
* Organizations with mature IT infrastructure
* Applications requiring strong service reusability

## Real-World Examples

* Large financial institutions integrating multiple banking systems
* Insurance companies integrating claims, underwriting, and billing
* Telecommunications companies coordinating various services
* Large enterprise resource planning (ERP) systems

---

# 7. Serverless Architecture

Developers write functions that execute in response to events without managing servers. The cloud provider automatically handles server provisioning, scaling, and management.

## What It Means

Serverless computing abstracts away the infrastructure layer from developers. Instead of managing servers or containers, developers write small functions (often 1-10KB of code) that execute in response to specific events. The cloud provider automatically scales resources up and down based on demand, and you only pay for the compute time actually used.

Note: "Serverless" doesn't mean no servers exist—it means developers don't manage them.

## Cloud Provider Services

**AWS Lambda:**
- Most mature serverless platform
- Supports Python, Node.js, Java, Go, .NET, Ruby
- Tight integration with AWS services

**Google Cloud Functions:**
- Simpler interface, less complex
- Good for event-driven workloads
- Supports Python, Node.js, Go

**Azure Functions:**
- Deep integration with Microsoft ecosystem
- Supports multiple languages
- Bindings for various Azure services

**Other Options:**
- IBM Cloud Functions
- Oracle Cloud Functions
- Alibaba Function Compute

## Billing Model

```
Cost = (Number of Requests) × (Compute Time in GB-seconds) × (Price per GB-second)

Example:
- 1,000,000 requests/month
- Average execution time: 200ms
- Memory: 256MB = 0.25 GB
- Price per GB-second: $0.0000166667

Cost = 1,000,000 × 0.2 × 0.25 × 0.0000166667 = $0.83/month
```

## Advantages

* **Auto Scaling** - Automatically handles traffic spikes
* **Pay Only for Usage** - No cost for idle servers, billing by 100ms increments
* **No Server Management** - No patching, updates, or infrastructure maintenance
* **Faster Deployment** - Deploy functions in seconds
* **High Availability** - Built-in redundancy and fault tolerance
* **Cost Effective** - Ideal for unpredictable or bursty workloads
* **Simplified Operations** - Less infrastructure to monitor and maintain

## Disadvantages

* **Cold Start Latency** - First invocation is slow (0.5-2 seconds), especially for Java
* **Execution Time Limits** - Max execution time (usually 15 minutes), not suitable for long processes
* **Vendor Lock-in** - Each cloud provider has different APIs and tools
* **Debugging Difficulty** - Harder to debug distributed serverless functions
* **Limited Storage** - No persistent storage on function (must use external services)
* **State Management** - Stateless by design, managing state is complex
* **Cold Start Costs** - Frequent cold starts can impact performance and cost
* **Limited Languages** - Only specific languages supported by each provider

## When to Use

* Event-driven workloads (file uploads, database changes)
* API backends (especially with variable traffic)
* Scheduled tasks and cron jobs
* Real-time data processing
* IoT applications
* Chatbots and AI applications
* Short-lived tasks (< 15 minutes)

## When NOT to Use

* Long-running processes (> 15 minutes)
* Applications requiring persistent connections
* Real-time graphics rendering
* Applications requiring consistent performance
* Cost-sensitive applications with constant traffic

## Real-World Examples

* **Image Processing** - Resize images when uploaded to cloud storage
* **API Backends** - REST APIs for mobile/web applications
* **Scheduled Reports** - Generate and send reports on a schedule
* **Log Processing** - Parse and index application logs
* **Chatbots** - Process user messages and generate responses
* **Data Transformation** - ETL jobs triggered by data changes

---

# 8. MVC Architecture

Model-View-Controller is a design pattern that separates an application into three interconnected components, each handling different aspects of the application logic.

## What It Means

MVC divides an application into three components:
- **Model**: Data and business logic
- **View**: User interface presentation
- **Controller**: Handles user input and coordinates between Model and View

This separation allows developers to work on different components independently and makes the application easier to scale and maintain.

## Detailed Explanation

**Model:**
- Represents data and business rules
- Independent of how data is presented or input
- Notifies Views of data changes
- Examples: User, Product, Order classes

**View:**
- Displays data from the Model
- Sends user input to Controller
- Can be HTML, JSON, XML
- Examples: JSP pages, Thymeleaf templates, React components

**Controller:**
- Receives user input from View
- Interprets user requests
- Updates Model accordingly
- Selects appropriate View
- Examples: Spring @Controller, Django views, Laravel controllers

## Popular MVC Frameworks

* **Django** (Python) - Full-featured framework with ORM
* **Spring MVC** (Java) - Enterprise framework with dependency injection
* **Laravel** (PHP) - Modern, elegant syntax
* **Ruby on Rails** (Ruby) - Convention over configuration
* **ASP.NET MVC** (.NET) - Microsoft's implementation

## Advantages

* **Organized Code** - Clear separation makes code easier to navigate
* **Easy Maintenance** - Changes in one component rarely affect others
* **Reusability** - Model can be used by multiple Views/Controllers
* **Testing** - Components can be tested independently
* **Scalability** - Easy to add new Views or Controllers
* **Parallel Development** - Multiple developers can work on different components
* **Clear Responsibilities** - Each component has well-defined role

## Disadvantages

* **Complexity for Simple Apps** - Overkill for very small applications
* **Tight Coupling Possible** - If not implemented carefully, components become coupled
* **Learning Curve** - Developers must understand the pattern
* **More Code** - More boilerplate code needed compared to monolithic approach
* **Testing Complexity** - Integration testing between components can be complex

## When to Use

* Web applications with clear separation of concerns
* Applications with multiple views of same data
* Team development environments
* Applications expected to grow over time
* Applications requiring regular maintenance updates

## Real-World Examples

* **Django Applications** - Instagram (uses Django), Spotify (uses Django)
* **Spring MVC Applications** - LinkedIn, Twitter (early versions)
* **Ruby on Rails** - GitHub, Shopify (originally)
* **Laravel Applications** - Many modern PHP web applications

---

# 9. Hexagonal Architecture (Ports & Adapters)

Hexagonal Architecture (also called Ports & Adapters) isolates core business logic from external systems. It allows business logic to be independent of frameworks, databases, and delivery mechanisms.

## What It Means

Hexagonal Architecture places the application core at the center, surrounded by ports and adapters. Ports are interfaces that define how external systems interact with the core. Adapters implement these ports to connect specific technologies to the core. This "hexagonal" design ensures the core never depends on external systems—external systems depend on the core.

## Key Concepts

**Core (Domain):**
- Pure business logic
- No dependencies on external frameworks
- No knowledge of databases, UIs, or web services
- Contains entities, value objects, and services

**Ports:**
- Interfaces defining contracts
- Input ports: APIs that other systems use
- Output ports: Dependencies on external systems
- Technology-agnostic

**Adapters:**
- Implement ports with specific technologies
- Convert between external formats and domain format
- REST adapter converts HTTP to domain objects
- Database adapter converts SQL to domain objects

## Advantages

* **Highly Testable** - Test business logic without databases or UIs
* **Framework Independent** - Swap frameworks without changing core logic
* **Easy Replacement** - Replace database, UI, or external service easily
* **Clear Dependencies** - External systems depend on core, not vice versa
* **Flexible** - Multiple clients (web, mobile, CLI) using same core
* **Maintainability** - Core logic is isolated and focused
* **Domain-Driven Design** - Natural fit with DDD principles
* **Rapid Prototyping** - Swap implementations easily during development

## Disadvantages

* **Complexity** - More layers and interfaces to manage
* **Over-engineering** - Overkill for simple applications
* **Learning Curve** - Requires understanding of ports and adapters concept
* **More Code** - More boilerplate code needed
* **Initial Development Slower** - More upfront architecture work

## When to Use

* Complex domain logic
* Applications requiring multiple interfaces (web, mobile, CLI)
* Long-lived projects
* Team development environments
* Applications using domain-driven design
* Applications requiring frequent framework changes
* Highly testable applications

## Implementation Example (Conceptual)

```
Project Structure:
├── domain/
│   ├── entities/          (Order, Product, User)
│   ├── value-objects/     (Money, Address)
│   └── services/          (OrderService, PaymentService)
├── ports/
│   ├── input-ports/       (CreateOrderRequest interface)
│   └── output-ports/      (OrderRepository interface)
├── adapters/
│   ├── in/
│   │   ├── rest/          (REST API adapter)
│   │   ├── graphql/       (GraphQL adapter)
│   │   └── cli/           (CLI adapter)
│   └── out/
│       ├── database/      (PostgreSQL adapter)
│       ├── cache/         (Redis adapter)
│       └── payment/       (Stripe adapter)
└── application/
    └── services/          (Use case orchestration)
```

## Real-World Examples

* DDD-based enterprise applications
* Microservices with clean architecture
* Applications using test-driven development
* Financial systems requiring high testability
* Healthcare systems with complex domain logic

---

# 10. Peer-to-Peer (P2P) Architecture

In peer-to-peer architecture, all nodes in the network have equal capabilities and responsibilities. Each node acts as both a client and a server, can store data, and can serve requests without a central authority.

## What It Means

Unlike client-server architecture where there's a central server, P2P distributes computation and data storage across all participating nodes. Each peer can initiate requests, serve requests, store data, and participate in decision-making. There is no single point of failure or authority.

**1. Unstructured P2P:**
- Nodes connect to random peers
- Simple to implement but less efficient
- Example: Gnutella

**2. Structured P2P (Distributed Hash Tables):**
- Nodes organized in specific topology
- Efficient content lookup
- Example: Chord, Kademlia

**3. Hybrid P2P:**
- Super-nodes act as coordinators
- Balance between centralization and decentralization
- Example: BitTorrent with trackers

## Technologies & Protocols

* **BitTorrent** - File sharing (torrents)
* **Blockchain/Bitcoin** - Distributed ledger, peer consensus
* **IPFS** (InterPlanetary File System) - Decentralized storage
* **Ethereum** - Distributed computing and smart contracts
* **Gnutella** - File sharing protocol
* **Kademlia** - DHT protocol (used in BitTorrent)
* **WebRTC** - Peer communication in browsers

## Advantages

* **No Central Server** - No single point of failure
* **Distributed Workload** - Computation and storage spread across peers
* **Scalability** - System grows stronger as more peers join
* **Resilience** - Network continues even if some peers go offline
* **Data Redundancy** - Multiple copies of data across the network
* **Censorship Resistance** - No central authority to shut down
* **Self-Healing** - Network automatically reorganizes when peers join/leave
* **Privacy** - No central entity collecting data

## Disadvantages

* **Security Challenges** - Malicious peers can attack or corrupt data
* **Complex Synchronization** - Ensuring consistency across peers is difficult
* **Network Overhead** - Peer discovery and message routing adds traffic
* **Difficult Debugging** - Hard to trace issues in distributed system
* **NAT Traversal** - Firewall/NAT issues complicate direct peer connections
* **Performance Variation** - Different peers have different speeds and reliability
* **Data Integrity** - Verifying data hasn't been tampered with
* **Bandwidth Requirements** - Each peer must upload and download data

## When to Use

* File sharing applications (torrents)
* Blockchain and cryptocurrency
* Decentralized social networks
* Distributed storage systems
* Mesh networks
* Decentralized applications (dApps)
* Collaborative computing projects
* Content delivery systems

## When NOT to Use

* Applications requiring strong central control
* Applications requiring immediate consistency
* Applications with security-critical data
* Real-time applications (low latency required)
* Applications with limited peer participation
* When regulatory compliance requires central authority

## Real-World Examples

* **BitTorrent** - File distribution (Linux ISOs, large files)
* **Bitcoin/Ethereum** - Cryptocurrency and blockchain
* **IPFS** - Decentralized web content distribution
* **Tor Network** - Anonymity and privacy
* **Mesh Networks** - Community internet projects
* **Syncthing** - Decentralized file synchronization
* **Discord** - Uses P2P for voice communication

## Security Considerations

**Challenges:**
- Sybil attacks (creating multiple fake identities)
- Free-riding (taking data without contributing)
- Data poisoning (corrupting shared data)
- Eclipse attacks (isolating nodes from network)

**Solutions:**
- Reputation systems
- Cryptographic verification
- Proof-of-work/Proof-of-stake
- Encrypted communication
- Byzantine fault tolerance

---

# Important Concepts in Software Architecture

1. Scalability

Scalability means a system’s ability to handle increasing
- users
- traffic
- requests
- data
without performance problems.

Real-Life Example
Imagine a restaurant.
- 10 customers → 2 staff members are enough
- 1000 customers → need more staff, tables, kitchen capacity
Software systems work similarly.

Types of Scalability
A. Vertical Scaling (Scale Up)
Increase power of a single server.
Example:
4 GB RAM → 16 GB RAM
2 CPU → 16 CPU

Advantages:
- Simple
- Easy migration

Disadvantages;
- Hardware limit exists
- Expensive
- Single point of failure

B. Horizontal Scaling (Scale Out)
Add more servers.
1 Server → 10 Servers
Example
Users
  ↓
Load Balancer
 ↓   ↓   ↓
S1  S2  S3

Advantages:
- Better reliability
- High availability
- Infinite scaling possibility

Disadvantages:
- Complex architecture
- Distributed system challenges

Example in Real Systems:
Netflix During peak hours, millions of users watch videos system automatically adds more servers This is scalability.

Scalability Techniques:
- Load balancing
- Caching
- Database sharding
- CDN
- Auto scaling
- Microservices
--------------------------------------------------------------
2. Availability

Availability means the system remains
- accessible
- operational
- online
most of the time.

Example

If a website runs:
99.99% uptime then downtime is very small yearly.

Real-Life Example
- Banking Application

Users expect:
- ATM working
- UPI transfers available
- mobile banking online
24/7 availability is critical.

How Availability is Achieved
Redundancy

Multiple servers exist.

Server A fails
↓
Server B continues
Multi-AZ Deployment

Deploy servers in multiple availability zones.

Health Checks

Automatically detect failed servers.

Failover Systems

Backup systems take over automatically.
-------------------------------------------------------------
3. Fault Tolerance

Fault tolerance means:
system continues working even when components fail.
Failure is expected in distributed systems.

Example:
Suppose Server 1 crashes But Server 2 continues serving users

Real-Life Example:
Aircraft Systems
Airplanes have:
- backup engines
- backup navigation
- backup communication
Software systems use similar ideas.

Example Architecture:
Load Balancer
   ↓
Server A 
Server B
Server C
If Server B fails Traffic goes to Server A and C
---------------------------------------------------
4. Load Balancing

Load balancing distributes traffic across multiple servers.

Without load balancing:
All users → One Server

Problem:
- server overload
- crashes
- slow performance

With Load Balancer
           Load Balancer
          ↙    ↓     ↘
       Server1 Server2 Server3

Traffic gets distributed evenly.

Benefits:
- Better performance
- High availability
- Fault tolerance
- Scalability

Types of Load Balancers:
Layer 4 Load Balancer
Works at:
TCP/UDP level

Example:
Amazon Web Services NLB

Layer 7 Load Balancer
Works at:
HTTP/HTTPS level
Can route based on:
- URL
- headers
- domains

Example:
- AWS ALB
- Nginx

Load Balancing Algorithms
Round Robin
Request1 → S1
Request2 → S2
Request3 → S3
Least Connections send to server with fewer active users.

Real-Life Example:
In Amazon Sale Event Millions of users visit simultaneously.Load balancers distribute traffic among thousands of servers.
--------------------------------------------
5. High Cohesion

Cohesion means related functionality should stay together.

High cohesion = focused modules.

Example
Good Design
UserService
- login
- register
- logout

All related to user management.

Bad Design
UserService
- login
- payment
- generateInvoice
- sendSMS

Too many unrelated responsibilities.

Benefits of High Cohesion:
- Easier maintenance
- Better readability
- Easier testing
- Reusable modules
- Real-Life Analogy

Hospital departments:
- Cardiology
- Neurology
- Orthopedics
- Each department focuses on related tasks.That is high cohesion.
--------------------------------
6. Low Coupling

Coupling means:
how dependent components are on each other.

Low coupling means:
components work independently changes in one module minimally affect others.

Bad Example (High Coupling)
OrderService directly modifies PaymentService internals

Problem:
changing payment system breaks order system

Good Example (Low Coupling)
OrderService → API → PaymentService
Only communicates through interfaces/APIs.

Benefits of Low Coupling:
- Easier changes
- Easier scaling
- Easier testing
- Better flexibility

Real-Life Example
USB Devices

Keyboard works independently.
You can replace keyboard, upgrade mouse without changing computer internals.That is low coupling.

High Cohesion + Low Coupling
This combination is a major software engineering goal.

Good Architecture:
- Authentication Service
- Payment Service
- Order Service
- Notification Service
Each:
- focused on one responsibility
- loosely connected

Bad Architecture:
One giant service doing everything

Problems:
- difficult debugging
- difficult scaling
- difficult deployment

