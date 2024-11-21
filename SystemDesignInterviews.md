


# interview ideaology
# RealWorld Applications System Designs[RealWorld Applications System Designs](#realworld-applications-system-designs)
# Custom System Desing Ideas

### Detailed Guide to System Design Interviews

System design interviews assess your ability to create scalable, efficient, and maintainable systems. Here’s a step-by-step guide to help you prepare and excel in these interviews:

#### 1. **Requirements Clarifications**

##### **Functional Requirements**
These are the core functionalities that your system must provide to meet user needs. They define what the system should do.

- **Examples:**
  - **User Management:** Sign up, login, profile management.
  - **Data Storage:** CRUD operations for data entities.
  - **Search Functionality:** Full-text search, filtering, sorting.

- **Questions to Ask:**
  - “What are the primary features of this system?”
  - “Are there any specific business rules or use cases we should consider?”
  - “What are the expected user interactions and workflows?”

##### **Non-Functional Requirements**
These define the quality attributes of the system, such as performance, scalability, and security. They are not directly related to specific features but to the overall user experience and system performance.

- **Examples:**
  - **Performance:** Latency should be less than 100ms for API responses.
  - **Scalability:** The system should handle up to 10,000 concurrent users.
  - **Availability:** The system should have 99.99% uptime.

- **Questions to Ask:**
  - “What are the performance requirements?”
  - “What are the uptime and availability expectations?”
  - “Are there specific security considerations we need to address?”

##### **Extended Requirements**
These are additional features or considerations that are desirable but not essential.

- **Examples:**
  - **Analytics:** Collecting and analyzing user behavior data.
  - **Monitoring:** Health checks and logging for system performance.
  - **Internationalization:** Support for multiple languages.

- **Questions to Ask:**
  - “Are there any analytics or monitoring requirements?”
  - “Do we need to support multiple languages or regions?”

#### 2. **Estimation and Constraints**

Estimate the scale of the system to guide design decisions. Understanding scale helps in making informed choices about architecture, database design, and performance optimizations.

- **Questions to Ask:**
  - “What is the estimated number of users or requests per second?”
  - “What is the expected data volume and growth rate?”
  - “What is the read/write ratio of the system?”
  - “Are there peak times or high traffic scenarios we need to plan for?”

#### 3. **Data Model Design**

Designing the database schema involves defining entities, their relationships, and how data is stored and accessed. This step is crucial for understanding data flow and ensuring efficient data operations.

- **Questions to Address:**
  - **Entities and Relationships:** Identify core entities (e.g., users, orders, products) and their relationships (e.g., one-to-many, many-to-many).
  - **Schema Design:** Define tables, fields, and indexes. Consider normalization and denormalization based on the use case.
  - **SQL vs. NoSQL:** Choose the database type based on requirements (e.g., relational databases for structured data, NoSQL for unstructured or semi-structured data).

- **Example Schema Design:**
  ```sql
  CREATE TABLE Users (
      user_id INT PRIMARY KEY,
      username VARCHAR(50),
      email VARCHAR(100),
      password_hash VARCHAR(255)
  );

  CREATE TABLE Orders (
      order_id INT PRIMARY KEY,
      user_id INT,
      order_date TIMESTAMP,
      FOREIGN KEY (user_id) REFERENCES Users(user_id)
  );
  ```

#### 4. **API Design**

Define the APIs that will interact with your system. This includes specifying endpoints, request/response formats, and error handling.

- **Example API Design:**
  ```typescript
  // API to create a new user
  POST /users
  Request Body: {
      username: string,
      email: string,
      password: string
  }
  Response: {
      user_id: number,
      username: string,
      email: string
  }
  ```

- **Questions to Consider:**
  - “What are the main API endpoints and their responsibilities?”
  - “What are the request and response formats?”
  - “How will we handle errors and edge cases?”

#### 5. **High-Level Component Design**

Identify and design the major components of your system, such as servers, load balancers, and databases. Create a high-level architecture diagram to visualize how these components interact.

- **Components to Consider:**
  - **Load Balancer:** Distributes incoming requests across multiple servers.
  - **API Gateway:** Manages API requests, provides routing, and handles authentication.
  - **Microservices:** Breaks down the system into smaller, independent services.

- **Questions to Explore:**
  - “Should we use a monolithic or microservices architecture?”
  - “What type of load balancing and caching strategies will be used?”
  - “How will data be partitioned and replicated?”

#### 6. **Detailed Design**

Dive into the specifics of major components, discussing how they will be implemented and integrated. This is where you demonstrate your technical expertise and understanding of best practices.

- **Questions to Address:**
  - “How will we implement data partitioning and replication?”
  - “What caching strategies will we use to improve performance?”
  - “How will we handle data consistency and availability?”

- **Example Caching Strategy:**
  - Use an in-memory cache (e.g., Redis) for frequently accessed data to reduce database load and improve response times.

#### 7. **Identify and Resolve Bottlenecks**

Discuss potential performance bottlenecks and how to address them. Consider scalability, reliability, and robustness of the system.

- **Questions to Address:**
  - “Are there any single points of failure in the system?”
  - “How can we scale the system to handle increased traffic?”
  - “What strategies will we use for load distribution and fault tolerance?”

- **Example Bottleneck Resolution:**
  - Implement database sharding to distribute data across multiple servers and reduce load on a single database.

### Additional Tips

- **Be Humble:** Acknowledge what you know and what you don’t. Use your knowledge and experience to navigate the discussion.
- **Company Research:** Understand the company’s technology stack and focus areas. Review their engineering blog or recent tech articles for insights.

This comprehensive approach will help you tackle system design interviews effectively, demonstrating your ability to design robust, scalable systems.


### RealWorld Applications System Designs 


# Uber

Let's design an [Uber](https://uber.com) like ride-hailing service, similar to services like [Lyft](https://www.lyft.com), [OLA Cabs](https://www.olacabs.com), etc.

## What is Uber?

Uber is a mobility service provider, allowing users to book rides and a driver to transport them in a way similar to a taxi. It is available on the web and mobile platforms such as Android and iOS.

## Requirements

Our system should meet the following requirements:

### Functional requirements

We will design our system for two types of users: Customers and Drivers.

**Customers**

- Customers should be able to see all the cabs in the vicinity with an ETA and pricing information.
- Customers should be able to book a cab to a destination.
- Customers should be able to see the location of the driver.

**Drivers**

- Drivers should be able to accept or deny the customer-requested ride.
- Once a driver accepts the ride, they should see the pickup location of the customer.
- Drivers should be able to mark the trip as complete on reaching the destination.

### Non-Functional requirements

- High reliability.
- High availability with minimal latency.
- The system should be scalable and efficient.

### Extended requirements

- Customers can rate the trip after it's completed.
- Payment processing.
- Metrics and analytics.

## Estimation and Constraints

Let's start with the estimation and constraints.

_Note: Make sure to check any scale or traffic-related assumptions with your interviewer._

### Traffic

Let us assume we have 100 million daily active users (DAU) with 1 million drivers and on average our platform enables 10 million rides daily.

If on average each user performs 10 actions (such as request a check available rides, fares, book rides, etc.) we will have to handle 1 billion requests daily.

$$
100 \space million \times 10 \space actions = 1 \space billion/day
$$

**What would be Requests Per Second (RPS) for our system?**

1 billion requests per day translate into 12K requests per second.

$$
\frac{1 \space billion}{(24 \space hrs \times 3600 \space seconds)} = \sim 12K \space requests/second
$$

### Storage

If we assume each message on average is 400 bytes, we will require about 400 GB of database storage every day.

$$
1 \space billion \times 400 \space bytes = \sim 400 \space GB/day
$$

And for 10 years, we will require about 1.4 PB of storage.

$$
400 \space GB \times 10 \space years \times 365 \space days = \sim 1.4 \space PB
$$

### Bandwidth

As our system is handling 400 GB of ingress every day, we will require a minimum bandwidth of around 5 MB per second.

$$
\frac{400 \space GB}{(24 \space hrs \times 3600 \space seconds)} = \sim 5 \space MB/second
$$

### High-level estimate

Here is our high-level estimate:

| Type                      | Estimate    |
| ------------------------- | ----------- |
| Daily active users (DAU)  | 100 million |
| Requests per second (RPS) | 12K/s       |
| Storage (per day)         | ~400 GB     |
| Storage (10 years)        | ~1.4 PB     |
| Bandwidth                 | ~5 MB/s     |

## Data model design

This is the general data model which reflects our requirements.

![uber-datamodel](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/uber/uber-datamodel.png)

We have the following tables:

**customers**

This table will contain a customer's information such as `name`, `email`, and other details.

**drivers**

This table will contain a driver's information such as `name`, `email`, `dob` and other details.

**trips**

This table represents the trip taken by the customer and stores data such as `source`, `destination`, and `status` of the trip.

**cabs**

This table stores data such as the registration number, and type (like Uber Go, Uber XL, etc.) of the cab that the driver will be driving.

**ratings**

As the name suggests, this table stores the `rating` and `feedback` for the trip.

**payments**

The payments table contains the payment-related data with the corresponding `tripID`.

### What kind of database should we use?

While our data model seems quite relational, we don't necessarily need to store everything in a single database, as this can limit our scalability and quickly become a bottleneck.

We will split the data between different services each having ownership over a particular table. Then we can use a relational database such as [PostgreSQL](https://www.postgresql.org) or a distributed NoSQL database such as [Apache Cassandra](https://cassandra.apache.org/_/index.html) for our use case.

## API design

Let us do a basic API design for our services:

### Request a Ride

Through this API, customers will be able to request a ride.

```tsx
requestRide(customerID: UUID, source: Tuple<float>, destination: Tuple<float>, cabType: Enum<string>, paymentMethod: Enum<string>): Ride
```

**Parameters**

Customer ID (`UUID`): ID of the customer.

Source (`Tuple<float>`): Tuple containing the latitude and longitude of the trip's starting location.

Destination (`Tuple<float>`): Tuple containing the latitude and longitude of the trip's destination.

**Returns**

Result (`Ride`): Associated ride information of the trip.

### Cancel the Ride

This API will allow customers to cancel the ride.

```tsx
cancelRide(customerID: UUID, reason?: string): boolean
```

**Parameters**

Customer ID (`UUID`): ID of the customer.

Reason (`UUID`): Reason for canceling the ride _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Accept or Deny the Ride

This API will allow the driver to accept or deny the trip.

```tsx
acceptRide(driverID: UUID, rideID: UUID): boolean
denyRide(driverID: UUID, rideID: UUID): boolean
```

**Parameters**

Driver ID (`UUID`): ID of the driver.

Ride ID (`UUID`): ID of the customer requested ride.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Start or End the Trip

Using this API, a driver will be able to start and end the trip.

```tsx
startTrip(driverID: UUID, tripID: UUID): boolean
endTrip(driverID: UUID, tripID: UUID): boolean
```

**Parameters**

Driver ID (`UUID`): ID of the driver.

Trip ID (`UUID`): ID of the requested trip.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Rate the Trip

This API will enable customers to rate the trip.

```tsx
rateTrip(customerID: UUID, tripID: UUID, rating: int, feedback?: string): boolean
```

**Parameters**

Customer ID (`UUID`): ID of the customer.

Trip ID (`UUID`): ID of the completed trip.

Rating (`int`): Rating of the trip.

Feedback (`string`): Feedback about the trip by the customer _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

## High-level design

Now let us do a high-level design of our system.

### Architecture

We will be using [microservices architecture](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) since it will make it easier to horizontally scale and decouple our services. Each service will have ownership of its own data model. Let's try to divide our system into some core services.

**Customer Service**

This service handles customer-related concerns such as authentication and customer information.

**Driver Service**

This service handles driver-related concerns such as authentication and driver information.

**Ride Service**

This service will be responsible for ride matching and quadtree aggregation. It will be discussed in detail separately.

**Trip Service**

This service handles trip-related functionality in our system.

**Payment Service**

This service will be responsible for handling payments in our system.

**Notification Service**

This service will simply send push notifications to the users. It will be discussed in detail separately.

**Analytics Service**

This service will be used for metrics and analytics use cases.

**What about inter-service communication and service discovery?**

Since our architecture is microservices-based, services will be communicating with each other as well. Generally, REST or HTTP performs well but we can further improve the performance using [gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#grpc) which is more lightweight and efficient.

[Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery) is another thing we will have to take into account. We can also use a service mesh that enables managed, observable, and secure communication between individual services.

_Note: Learn more about [REST, GraphQL, gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc) and how they compare with each other._

### How is the service expected to work?

Here's how our service is expected to work:

![uber-working](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/uber/uber-working.png)

1. Customer requests a ride by specifying the source, destination, cab type, payment method, etc.
2. Ride service registers this request, finds nearby drivers, and calculates the estimated time of arrival (ETA).
3. The request is then broadcasted to the nearby drivers for them to accept or deny.
4. If the driver accepts, the customer is notified about the live location of the driver with the estimated time of arrival (ETA) while they wait for pickup.
5. The customer is picked up and the driver can start the trip.
6. Once the destination is reached, the driver will mark the ride as complete and collect payment.
7. After the payment is complete, the customer can leave a rating and feedback for the trip if they like.

### Location Tracking

How do we efficiently send and receive live location data from the client (customers and drivers) to our backend? We have two different options:

**Pull model**

The client can periodically send an HTTP request to servers to report its current location and receive ETA and pricing information. This can be achieved via something like [Long polling](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#long-polling).

**Push model**

The client opens a long-lived connection with the server and once new data is available it will be pushed to the client. We can use [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) or [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) for this.

The pull model approach is not scalable as it will create unnecessary request overhead on our servers and most of the time the response will be empty, thus wasting our resources. To minimize latency, using the push model with [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) is a better choice because then we can push data to the client once it's available without any delay, given that the connection is open with the client. Also, WebSockets provide full-duplex communication, unlike [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) which are only unidirectional.

Additionally, the client application should have some sort of background job mechanism to ping GPS location while the application is in the background.

_Note: Learn more about [Long polling, WebSockets, Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events)._

### Ride Matching

We need a way to efficiently store and query nearby drivers. Let's explore different solutions we can incorporate into our design.

**SQL**

We already have access to the latitude and longitude of our customers, and with databases like [PostgreSQL](https://www.postgresql.org) and [MySQL](https://www.mysql.com) we can perform a query to find nearby driver locations given a latitude and longitude (X, Y) within a radius (R).

```sql
SELECT * FROM locations WHERE lat BETWEEN X-R AND X+R AND long BETWEEN Y-R AND Y+R
```

However, this is not scalable, and performing this query on large datasets will be quite slow.

**Geohashing**

[Geohashing](https://karanpratapsingh.com/courses/system-design/geohashing-and-quadtrees#geohashing) is a [geocoding](https://en.wikipedia.org/wiki/Address_geocoding) method used to encode geographic coordinates such as latitude and longitude into short alphanumeric strings. It was created by [Gustavo Niemeyer](https://twitter.com/gniemeyer) in 2008.

Geohash is a hierarchical spatial index that uses Base-32 alphabet encoding, the first character in a geohash identifies the initial location as one of the 32 cells. This cell will also contain 32 cells. This means that to represent a point, the world is recursively divided into smaller and smaller cells with each additional bit until the desired precision is attained. The precision factor also determines the size of the cell.

![geohashing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/geohashing.png)

For example, San Francisco with coordinates `37.7564, -122.4016` can be represented in geohash as `9q8yy9mf`.

Now, using the customer's geohash we can determine the nearest available driver by simply comparing it with the driver's geohash. For better performance, we will index and store the geohash of the driver in memory for faster retrieval.

The cell sizes of the geohashes of different lengths are as follows:

| Geohash length | Cell width | Cell height |
| -------------- | ---------- | ----------- |
| 1              | 5000 km    | 5000 km     |
| 2              | 1250 km    | 1250 km     |
| 3              | 156 km     | 156 km      |
| 4              | 39.1 km    | 19.5 km     |
| 5              | 4.89 km    | 4.89 km     |
| 6              | 1.22 km    | 0.61 km     |
| 7              | 153 m      | 153 m       |
| 8              | 38.2 m     | 19.1 m      |
| 9              | 4.77 m     | 4.77 m      |
| 10             | 1.19 m     | 0.596 m     |
| 11             | 149 mm     | 149 mm      |
| 12             | 37.2 mm    | 18.6 mm     |

**Quadtrees**

A [Quadtree](https://karanpratapsingh.com/courses/system-design/geohashing-and-quadtrees#quadtrees) is a tree data structure in which each internal node has exactly four children. They are often used to partition a two-dimensional space by recursively subdividing it into four quadrants or regions. Each child or leaf node stores spatial information. Quadtrees are the two-dimensional analog of [Octrees](https://en.wikipedia.org/wiki/Octree) which are used to partition three-dimensional space.

![quadtree](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/quadtree.png)

Quadtrees enable us to search points within a two-dimensional range efficiently, where those points are defined as latitude/longitude coordinates or as cartesian (x, y) coordinates.

We can save further computation by only subdividing a node after a certain threshold.

![quadtree-subdivision](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/quadtree-subdivision.png)

[Quadtree](https://karanpratapsingh.com/courses/system-design/geohashing-and-quadtrees#quadtrees) seems perfect for our use case, we can update the Quadtree every time we receive a new location update from the driver. To reduce the load on the quadtree servers we can use an in-memory datastore such as [Redis](https://redis.io) to cache the latest updates. And with the application of mapping algorithms such as the [Hilbert curve](https://en.wikipedia.org/wiki/Hilbert_curve), we can perform efficient range queries to find nearby drivers for the customer.

**What about race conditions?**

Race conditions can easily occur when a large number of customers will be requesting rides simultaneously. To avoid this, we can wrap our ride matching logic in a [Mutex](<https://en.wikipedia.org/wiki/Lock_(computer_science)>) to avoid any race conditions. Furthermore, every action should be transactional in nature.

_For more details, refer to [Transactions](https://karanpratapsingh.com/courses/system-design/transactions) and [Distributed Transactions](https://karanpratapsingh.com/courses/system-design/distributed-transactions)._

**How to find the best drivers nearby?**

Once we have a list of nearby drivers from the Quadtree servers, we can perform some sort of ranking based on parameters like average ratings, relevance, past customer feedback, etc. This will allow us to broadcast notifications to the best available drivers first.

**Dealing with high demand**

In cases of high demand, we can use the concept of Surge Pricing. Surge pricing is a dynamic pricing method where prices are temporarily increased as a reaction to increased demand and mostly limited supply. This surge price can be added to the base price of the trip.

_For more details, learn how [surge pricing works](https://www.uber.com/us/en/drive/driver-app/how-surge-works) with Uber._

### Payments

Handling payments at scale is challenging, to simplify our system we can use a third-party payment processor like [Stripe](https://stripe.com) or [PayPal](https://www.paypal.com). Once the payment is complete, the payment processor will redirect the user back to our application and we can set up a [webhook](https://en.wikipedia.org/wiki/Webhook) to capture all the payment-related data.

### Notifications

Push notifications will be an integral part of our platform. We can use a message queue or a message broker such as [Apache Kafka](https://kafka.apache.org) with the notification service to dispatch requests to [Firebase Cloud Messaging (FCM)](https://firebase.google.com/docs/cloud-messaging) or [Apple Push Notification Service (APNS)](https://developer.apple.com/documentation/usernotifications) which will handle the delivery of the push notifications to user devices.

_For more details, refer to the [WhatsApp](https://karanpratapsingh.com/courses/system-design/whatsapp#notifications) system design where we discuss push notifications in detail._

## Detailed design

It's time to discuss our design decisions in detail.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can shard our database either based on existing [partition schemes](https://karanpratapsingh.com/courses/system-design/sharding#partitioning-criteria) or regions. If we divide the locations into regions using let's say zip codes, we can effectively store all the data in a given region on a fixed node. But this can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

_For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing)._

### Metrics and Analytics

Recording analytics and metrics is one of our extended requirements. We can capture the data from different services and run analytics on the data using [Apache Spark](https://spark.apache.org) which is an open-source unified analytics engine for large-scale data processing. Additionally, we can store critical metadata in the views table to increase data points within our data.

### Caching

In a location services-based platform, caching is important. We have to be able to cache the recent locations of the customers and drivers for fast retrieval. We can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) but what kind of cache eviction policy would best fit our needs?

**Which cache eviction policy to use?**

[Least Recently Used (LRU)](<https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)>) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

_For more details, refer to [Caching](https://karanpratapsingh.com/courses/system-design/caching)._



# Netflix 

Netflix is a subscription-based streaming service that allows its members to watch TV shows and movies on an internet-connected device. It is available on platforms such as the Web, iOS, Android, TV, etc.

## Requirements

Our system should meet the following requirements:

### Functional requirements

- Users should be able to stream and share videos.
- The content team (or users in YouTube's case) should be able to upload new videos (movies, tv shows episodes, and other content).
- Users should be able to search for videos using titles or tags.
- Users should be able to comment on a video similar to YouTube.

### Non-Functional requirements

- High availability with minimal latency.
- High reliability, no uploads should be lost.
- The system should be scalable and efficient.

### Extended requirements

- Certain content should be [geo-blocked](https://en.wikipedia.org/wiki/Geo-blocking).
- Resume video playback from the point user left off.
- Record metrics and analytics of videos.

## Estimation and Constraints

Let's start with the estimation and constraints.

_Note: Make sure to check any scale or traffic-related assumptions with your interviewer._

### Traffic

This will be a read-heavy system, let us assume we have 1 billion total users with 200 million daily active users (DAU), and on average each user watches 5 videos a day. This gives us 1 billion videos watched per day.

$$
200 \space million \times 5 \space videos = 1 \space billion/day
$$

Assuming a `200:1` read/write ratio, about 5 million videos will be uploaded every day.

$$
\frac{1}{200} \times 1 \space billion = 5 \space million/day
$$

**What would be Requests Per Second (RPS) for our system?**

1 billion requests per day translate into 12K requests per second.

$$
\frac{1 \space billion}{(24 \space hrs \times 3600 \space seconds)} = \sim 12K \space requests/second
$$

### Storage

If we assume each video is 100 MB on average, we will require about 500 TB of storage every day.

$$
5 \space million \times 100 \space MB = 500 \space TB/day
$$

And for 10 years, we will require an astounding 1,825 PB of storage.

$$
500 \space TB \times 365 \space days \times 10 \space years = \sim 1,825 \space PB
$$

### Bandwidth

As our system is handling 500 TB of ingress every day, we will require a minimum bandwidth of around 5.8 GB per second.

$$
\frac{500 \space TB}{(24 \space hrs \times 3600 \space seconds)} = \sim 5.8 \space GB/second
$$

### High-level estimate

Here is our high-level estimate:

| Type                      | Estimate    |
| ------------------------- | ----------- |
| Daily active users (DAU)  | 200 million |
| Requests per second (RPS) | 12K/s       |
| Storage (per day)         | ~500 TB     |
| Storage (10 years)        | ~1,825 PB   |
| Bandwidth                 | ~5.8 GB/s   |

## Data model design

This is the general data model which reflects our requirements.

![netflix-datamodel](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/netflix-datamodel.png)

We have the following tables:

**users**

This table will contain a user's information such as `name`, `email`, `dob`, and other details.

**videos**

As the name suggests, this table will store videos and their properties such as `title`, `streamURL`, `tags`, etc. We will also store the corresponding `userID`.

**tags**

This table will simply store tags associated with a video.

**views**

This table helps us to store all the views received on a video.

**comments**

This table stores all the comments received on a video (like YouTube).

### What kind of database should we use?

While our data model seems quite relational, we don't necessarily need to store everything in a single database, as this can limit our scalability and quickly become a bottleneck.

We will split the data between different services each having ownership over a particular table. Then we can use a relational database such as [PostgreSQL](https://www.postgresql.org) or a distributed NoSQL database such as [Apache Cassandra](https://cassandra.apache.org/_/index.html) for our use case.

## API design

Let us do a basic API design for our services:

### Upload a video

Given a byte stream, this API enables video to be uploaded to our service.

```tsx
uploadVideo(title: string, description: string, data: Stream<byte>, tags?: string[]): boolean
```

**Parameters**

Title (`string`): Title of the new video.

Description (`string`): Description of the new video.

Data (`byte[]`): Byte stream of the video data.

Tags (`string[]`): Tags for the video _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Streaming a video

This API allows our users to stream a video with the preferred codec and resolution.

```tsx
streamVideo(videoID: UUID, codec: Enum<string>, resolution: Tuple<int>, offset?: int): VideoStream
```

**Parameters**

Video ID (`UUID`): ID of the video that needs to be streamed.

Codec (`Enum<string>`): Required [codec](https://en.wikipedia.org/wiki/Video_codec) of the requested video, such as `h.265`, `h.264`, `VP9`, etc.

Resolution (`Tuple<int>`): [Resolution](https://en.wikipedia.org/wiki/Display_resolution) of the requested video.

Offset (`int`): Offset of the video stream in seconds to stream data from any point in the video _(optional)_.

**Returns**

Stream (`VideoStream`): Data stream of the requested video.

### Search for a video

This API will enable our users to search for a video based on its title or tags.

```tsx
searchVideo(query: string, nextPage?: string): Video[]
```

**Parameters**

Query (`string`): Search query from the user.

Next Page (`string`): Token for the next page, this can be used for pagination _(optional)_.

**Returns**

Videos (`Video[]`): All the videos available for a particular search query.

### Add a comment

This API will allow our users to post a comment on a video (like YouTube).

```tsx
comment(videoID: UUID, comment: string): boolean
```

**Parameters**

VideoID (`UUID`): ID of the video user wants to comment on.

Comment (`string`): The text content of the comment.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

## High-level design

Now let us do a high-level design of our system.

### Architecture

We will be using [microservices architecture](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) since it will make it easier to horizontally scale and decouple our services. Each service will have ownership of its own data model. Let's try to divide our system into some core services.

**User Service**

This service handles user-related concerns such as authentication and user information.

**Stream Service**

The stream service will handle video streaming-related functionality.

**Search Service**

The service is responsible for handling search-related functionality. It will be discussed in detail separately.

**Media service**

This service will handle the video uploads and processing. It will be discussed in detail separately.

**Analytics Service**

This service will be used for metrics and analytics use cases.

**What about inter-service communication and service discovery?**

Since our architecture is microservices-based, services will be communicating with each other as well. Generally, REST or HTTP performs well but we can further improve the performance using [gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#grpc) which is more lightweight and efficient.

[Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery) is another thing we will have to take into account. We can also use a service mesh that enables managed, observable, and secure communication between individual services.

_Note: Learn more about [REST, GraphQL, gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc) and how they compare with each other._

### Video processing

![video-processing-pipeline](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/video-processing-pipeline.png)

There are so many variables in play when it comes to processing a video. For example, an average data size of two-hour raw 8K footage from a high-end camera can easily be up to 4 TB, thus we need to have some kind of processing to reduce both storage and delivery costs.

Here's how we can process videos once they're uploaded by the content team (or users in YouTube's case) and are queued for processing in our [message queue](https://karanpratapsingh.com/courses/system-design/message-queues).

Let's discuss how this works:

- **File Chunker**

![file-chunking](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/file-chunking.png)

This is the first step of our processing pipeline. File chunking is the process of splitting a file into smaller pieces called chunks. It can help us eliminate duplicate copies of repeating data on storage, and reduces the amount of data sent over the network by only selecting changed chunks.

Usually, a video file can be split into equal size chunks based on timestamps but Netflix instead splits chunks based on scenes. This slight variation becomes a huge factor for a better user experience since whenever the client requests a chunk from the server, there is a lower chance of interruption as a complete scene will be retrieved.

- **Content Filter**

This step checks if the video adheres to the content policy of the platform. This can be pre-approved as in the case of Netflix according to [content rating](https://en.wikipedia.org/wiki/Motion_picture_content_rating_system) of the media or can be strictly enforced like by YouTube.

This entire process is done by a machine learning model which performs copyright, piracy, and NSFW checks. If issues are found, we can push the task to a [dead-letter queue (DLQ)](https://karanpratapsingh.com/courses/system-design/message-queues#dead-letter-queues) and someone from the moderation team can do further inspection.

- **Transcoder**

[Transcoding](https://en.wikipedia.org/wiki/Transcoding) is a process in which the original data is decoded to an intermediate uncompressed format, which is then encoded into the target format. This process uses different [codecs](https://en.wikipedia.org/wiki/Video_codec) to perform bitrate adjustment, image downsampling, or re-encoding the media.

This results in a smaller size file and a much more optimized format for the target devices. Standalone solutions such as [FFmpeg](https://ffmpeg.org) or cloud-based solutions like [AWS Elemental MediaConvert](https://aws.amazon.com/mediaconvert) can be used to implement this step of the pipeline.

- **Quality Conversion**

This is the last step of the processing pipeline and as the name suggests, this step handles the conversion of the transcoded media from the previous step into different resolutions such as 4K, 1440p, 1080p, 720p, etc.

It allows us to fetch the desired quality of the video as per the user's request, and once the media file finishes processing, it gets uploaded to a distributed file storage such as [HDFS](https://karanpratapsingh.com/courses/system-design/storage#hdfs), [GlusterFS](https://www.gluster.org), or an [object storage](https://karanpratapsingh.com/courses/system-design/storage#object-storage) such as [Amazon S3](https://aws.amazon.com/s3) for later retrieval during streaming.

_Note: We can add additional steps such as subtitles and thumbnails generation as part of our pipeline._

**Why are we using a message queue?**

Processing videos as a long-running task and using a [message queue](https://karanpratapsingh.com/courses/system-design/message-queues) makes much more sense. It also decouples our video processing pipeline from the upload functionality. We can use something like [Amazon SQS](https://aws.amazon.com/sqs) or [RabbitMQ](https://www.rabbitmq.com) to support this.

### Video streaming

Video streaming is a challenging task from both the client and server perspectives. Moreover, internet connection speeds vary quite a lot between different users. To make sure users don't re-fetch the same content, we can use a [Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network).

Netflix takes this a step further with its [Open Connect](https://openconnect.netflix.com) program. In this approach, they partner with thousands of Internet Service Providers (ISPs) to localize their traffic and deliver their content more efficiently.

**What is the difference between Netflix's Open Connect and a traditional Content Delivery Network (CDN)?**

Netflix Open Connect is a purpose-built [Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network) responsible for serving Netflix's video traffic. Around 95% of the traffic globally is delivered via direct connections between Open Connect and the ISPs their customers use to access the internet.

Currently, they have Open Connect Appliances (OCAs) in over 1000 separate locations around the world. In case of issues, Open Connect Appliances (OCAs) can failover, and the traffic can be re-routed to Netflix servers.

Additionally, we can use [Adaptive bitrate streaming](https://en.wikipedia.org/wiki/Adaptive_bitrate_streaming) protocols such as [HTTP Live Streaming (HLS)](https://en.wikipedia.org/wiki/HTTP_Live_Streaming) which is designed for reliability and it dynamically adapts to network conditions by optimizing playback for the available speed of the connections.

Lastly, for playing the video from where the user left off (part of our extended requirements), we can simply use the `offset` property we stored in the `views` table to retrieve the scene chunk at that particular timestamp and resume the playback for the user.

### Searching

Sometimes traditional DBMS are not performant enough, we need something which allows us to store, search, and analyze huge volumes of data quickly and in near real-time and give results within milliseconds. [Elasticsearch](https://www.elastic.co) can help us with this use case.

[Elasticsearch](https://www.elastic.co) is a distributed, free and open search and analytics engine for all types of data, including textual, numerical, geospatial, structured, and unstructured. It is built on top of [Apache Lucene](https://lucene.apache.org).

**How do we identify trending content?**

Trending functionality will be based on top of the search functionality. We can cache the most frequently searched queries in the last `N` seconds and update them every `M` seconds using some sort of batch job mechanism.

### Sharing

Sharing content is an important part of any platform, for this, we can have some sort of URL shortener service in place that can generate short URLs for the users to share.

_For more details, refer to the [URL Shortener](https://karanpratapsingh.com/courses/system-design/url-shortener) system design._

## Detailed design

It's time to discuss our design decisions in detail.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can use partitions schemes such as:

- Hash-Based Partitioning
- List-Based Partitioning
- Range Based Partitioning
- Composite Partitioning

The above approaches can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

_For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing)._

### Geo-blocking

Platforms like Netflix and YouTube use [Geo-blocking](https://en.wikipedia.org/wiki/Geo-blocking) to restrict content in certain geographical areas or countries. This is primarily done due to legal distribution laws that Netflix has to adhere to when they make a deal with the production and distribution companies. In the case of YouTube, this will be controlled by the user during the publishing of the content.

We can determine the user's location either using their [IP](https://karanpratapsingh.com/courses/system-design/ip) or region settings in their profile then use services like [Amazon CloudFront](https://aws.amazon.com/cloudfront) which supports a geographic restrictions feature or a [geolocation routing policy](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-geo.html) with [Amazon Route53](https://aws.amazon.com/route53) to restrict the content and re-route the user to an error page if the content is not available in that particular region or country.

### Recommendations

Netflix uses a machine learning model which uses the user's viewing history to predict what the user might like to watch next, an algorithm like [Collaborative Filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) can be used.

However, Netflix (like YouTube) uses its own algorithm called Netflix Recommendation Engine which can track several data points such as:

- User profile information like age, gender, and location.
- Browsing and scrolling behavior of the user.
- Time and date a user watched a title.
- The device which was used to stream the content.
- The number of searches and what terms were searched.

_For more detail, refer to [Netflix recommendation research](https://research.netflix.com/research-area/recommendations)._

### Metrics and Analytics

Recording analytics and metrics is one of our extended requirements. We can capture the data from different services and run analytics on the data using [Apache Spark](https://spark.apache.org) which is an open-source unified analytics engine for large-scale data processing. Additionally, we can store critical metadata in the views table to increase data points within our data.

### Caching

In a streaming platform, caching is important. We have to be able to cache as much static media content as possible to improve user experience. We can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) but what kind of cache eviction policy would best fit our needs?

**Which cache eviction policy to use?**

[Least Recently Used (LRU)](<https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)>) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

_For more details, refer to [Caching](https://karanpratapsingh.com/courses/system-design/caching)._

### Media streaming and storage

As most of our storage space will be used for storing media files such as thumbnails and videos. Per our discussion earlier, the media service will be handling both the upload and processing of media files.

We will use distributed file storage such as [HDFS](https://karanpratapsingh.com/courses/system-design/storage#hdfs), [GlusterFS](https://www.gluster.org), or an [object storage](https://karanpratapsingh.com/courses/system-design/storage#object-storage) such as [Amazon S3](https://aws.amazon.com/s3) for storage and streaming of the content.

### Content Delivery Network (CDN)

[Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network) increases content availability and redundancy while reducing bandwidth costs. Generally, static files such as images, and videos are served from CDN. We can use services like [Amazon CloudFront](https://aws.amazon.com/cloudfront) or [Cloudflare CDN](https://www.cloudflare.com/cdn) for this use case.



### WhatsApp System Design

Building a system like WhatsApp involves several core components and design principles to ensure it supports billions of users, with the scalability, availability, and efficiency required. Let's break it down:

## Functional Overview

1. **One-on-one chat**: Support for direct messaging between two users.
2. **Group chats**: Allow multiple users (up to 100) to participate in a conversation.
3. **File sharing**: Support for image, video, and other file sharing.

## Non-functional Overview

1. **High Availability**: The system must remain available at all times with minimal downtime.
2. **Scalability**: The system must scale to accommodate billions of users with a dynamic increase in traffic.
3. **Minimal Latency**: Deliver messages in real-time with low response times.
4. **Durability**: Ensures messages and media are persistently stored and not lost.

## Extended Features

- **Receipts**: Sent, delivered, and read indicators for messages.
- **Last Seen**: Display the last active time of users.
- **Push Notifications**: Inform users about new messages and other updates.

---

## Estimations and Constraints

### Traffic

- **50M Daily Active Users (DAU)**, sending **40 messages per day each**.
- **Total Messages**: 2 billion messages per day.
- **Media Files**: 5% of messages are media (100M media files per day).

### Requests Per Second (RPS)
- Approx. 24K messages per second: 
  \[
  \frac{2B \space messages}{24 \space hours \times 3600 \space seconds} \approx 24K/s
  \]

### Storage
- **Message Storage**: 200GB of message data per day (assuming each message is ~100 bytes).
- **Media Storage**: 10TB of media storage per day (assuming each media file is ~100KB).
- **10-Year Estimate**: Total storage of ~38 PB.
  
### Bandwidth
- **10.2TB of data per day** requires about 120MB/sec of bandwidth.

---

## Data Model Design

### Tables Overview

1. **Users**: Stores user information (`userID`, `phoneNumber`, etc.).
2. **Messages**: Stores messages (`messageID`, `type`, `content`, `timestamp`, etc.).
3. **Chats**: Represents private conversations between two users (`chatID`, `lastMessage`, etc.).
4. **Users_Chats**: Maps users to chats (many-to-many relationship).
5. **Groups**: Represents group conversations (`groupID`, `groupName`, etc.).
6. **Users_Groups**: Maps users to groups (many-to-many relationship).

---

### Database Choice

- **Relational Database (PostgreSQL)** for structured data (users, chats, groups).
- **NoSQL (Cassandra)** for handling massive scale and distributed nature (messages, media storage).
- **Media Storage**: A separate storage solution like **Amazon S3** or **Google Cloud Storage** for media files.

---

## API Design

1. **Get All Chats/Groups**: Retrieve all chat or group IDs for a user.
   ```tsx
   getAll(userID: UUID): Chat[] | Group[]
   ```

2. **Get Messages**: Retrieve all messages for a chat or group.
   ```tsx
   getMessages(userID: UUID, channelID: UUID): Message[]
   ```

3. **Send Message**: Send a message from a user to a chat or group.
   ```tsx
   sendMessage(userID: UUID, channelID: UUID, message: Message): boolean
   ```

4. **Join/Leave Group**: Add or remove a user from a group.
   ```tsx
   joinGroup(userID: UUID, groupID: UUID): boolean
   leaveGroup(userID: UUID, groupID: UUID): boolean
   ```

---

## Core Components

1. **Real-time Communication**: Leverage **WebSockets** for maintaining long-lived connections between clients and servers for real-time message delivery.
2. **Message Queue**: Use a distributed messaging system like **Apache Kafka** to handle messaging traffic and ensure durability.
3. **Caching Layer**: Use **Redis** or **Memcached** for quick lookups (e.g., user status, last seen).
4. **Load Balancing**: Distribute incoming traffic efficiently across multiple servers using **load balancers** (e.g., Nginx, HAProxy).
5. **File Storage**: Media files can be stored on a distributed storage solution like **Amazon S3** or **Google Cloud Storage**.

---

## Advanced Features

1. **Message Delivery Status**: 
   - Track message delivery with different statuses: Sent, Delivered, Read.
   - Can be stored as metadata in the **messages** table.

2. **Last Seen and Online Status**: 
   - Use a combination of database and **Redis** for storing and updating users' online presence.

3. **Push Notifications**:
   - Integrate with **Apple Push Notification Service (APNS)** and **Firebase Cloud Messaging (FCM)** for sending push notifications on mobile.

---

## Scaling and Bottlenecks

To handle scaling and avoid bottlenecks:

1. **Multiple Instances**: Run multiple instances of services (message servers, WebSocket servers).
2. **Load Balancers**: Use load balancers to distribute traffic evenly across servers.
3. **Sharding**: Partition users across different databases based on user ID (hash-based partitioning) to prevent any single database from becoming a bottleneck.
4. **Replication**: Use **read replicas** to distribute read traffic in the database and ensure high availability.
5. **Backup Solutions**: Implement automatic backup and recovery strategies for message data and media.

By addressing these key considerations, we can ensure WhatsApp-like systems scale effectively, perform well under heavy loads, and provide users with real-time messaging.
## High-level design

To design a scalable and efficient WhatsApp-like service, we'll break down the system into microservices, each with a clear responsibility. Here's an overview of our architecture and design choices for key features.

### Architecture

We will adopt a **microservices architecture**, which allows for independent scalability and efficient management of different functionalities. Each service will have its own data store and API. Here are the core services:

1. **User Service**: Handles user authentication, registration, and profile management.
2. **Chat Service**: Manages one-on-one and group chats, including real-time messaging using WebSockets.
3. **Notification Service**: Sends notifications when users receive messages or updates.
4. **Presence Service**: Tracks the online status and last seen time for users.
5. **Media Service**: Handles file uploads and media content, such as images and videos.
6. **Message Queue**: Ensures ordered delivery of messages and manages notifications.
7. **Cache**: Using Redis or Memcached for tracking online users and presence status.

Each of these services will communicate via **gRPC** or **HTTP** for efficient, lightweight inter-service communication.

### Real-time Messaging: WebSockets vs Long Polling

We will use **WebSockets** to handle real-time communication for chat messages. WebSockets provide full-duplex communication, making them ideal for real-time applications where low latency and bidirectional communication are essential. Clients will establish a persistent connection with the server, which allows immediate message delivery when a new message is available.

In contrast, long polling would create additional load and latency, as clients repeatedly request updates from the server even when there are no new messages.

### Presence Service and Last Seen

The **Presence Service** will track whether users are online, along with their last seen timestamp. We will implement two strategies:

1. **Heartbeat Mechanism**: The client will send a ping to the server every few seconds, confirming the user is still online. This is low-overhead and gives an accurate reflection of online status.
2. **Lazy Update**: We can track user activity (e.g., message sent, chat opened) and mark users as inactive if they haven’t performed any action within a defined window (e.g., 30 seconds).

We will store the online status and last seen data in a **Redis** or **Memcached** cache for fast access.

### Notifications

When a user receives a message and is not online, the **Notification Service** will send push notifications using a **Message Queue** (e.g., Amazon SQS, RabbitMQ). The queue allows us to decouple the notification process from the main chat service, reducing delays.

- **Message Queue**: Ensures that notifications are processed in the correct order and reliably delivered at least once.
- **Firebase Cloud Messaging (FCM)** or **Apple Push Notification Service (APNS)** will deliver the notifications depending on the user’s device.

The flow is as follows:
1. The **Chat Service** adds a notification event to the message queue when a message is sent.
2. The **Notification Service** consumes this event and sends the notification via FCM or APNS based on the device type.

### Read Receipts and Delivery Confirmation

- **Delivery Acknowledgment (ACK)**: When a message is delivered, the server will receive an ACK from the client, updating the `deliveredAt` field in the database.
- **Read Receipts**: When the user opens the message or chat, the client sends a signal to update the `seenAt` field. Both delivery and read receipts will be managed asynchronously to avoid blocking the user interface.

### Scalability and Performance

- **Horizontal Scalability**: Each service (e.g., chat, notification, media) can scale independently based on load.
- **Service Discovery**: Using a **service mesh** (e.g., Istio) for routing and service discovery ensures that services can efficiently communicate without hard-coded locations.
- **Caching**: Presence, last seen, and online status will be stored in a cache to reduce load on the database.
  
This design allows us to meet the core requirements, ensuring scalability, real-time communication, and efficient resource usage.
### System Design Breakdown

#### 1. **Data Partitioning**
   - **Why:** To scale out databases for performance and manageability.
   - **Approach:** Horizontal partitioning (Sharding).
     - **Options:**
       - Hash-Based
       - List-Based
       - Range-Based
       - Composite Partitioning
     - **Solution:** Consistent Hashing to ensure even load distribution across shards.

#### 2. **Caching**
   - **Why:** Reduce load on databases and improve response times.
   - **Key Points:**
     - Cache older, less frequently accessed messages to reduce spikes.
     - Implement pagination for fetching older messages in group chats.
     - Use **LRU (Least Recently Used)** as a cache eviction policy.
     - **Cache Miss Handling:** Query database and refresh cache.
     - **Tools:** Redis or Memcached.

#### 3. **Media Access & Storage**
   - **Why:** Large-scale media storage.
   - **Solution:** Use object storage for scalable media storage.
     - **Options:** Amazon S3, Azure Blob, or Google Cloud Storage.
     - **Fun Fact:** Media can be deleted from servers after it's downloaded.
     - **Optimization:** Introduce media compression to reduce storage costs.

#### 4. **Content Delivery Network (CDN)**
   - **Why:** Improve availability and reduce bandwidth costs.
   - **Tools:** Amazon CloudFront, Cloudflare CDN.

#### 5. **API Gateway**
   - **Why:** Handle multiple communication protocols and manage API requests.
   - **Features:**
     - Authentication, Authorization.
     - Rate Limiting, Throttling.
     - API versioning.
   - **Tools:** Amazon API Gateway, Azure API Gateway.

#### 6. **Bottlenecks & Solutions**
   - **Service Failures:**
     - Run multiple instances of each service.
     - Use load balancers between clients, services, databases, and caches.
   - **Database Load:**
     - Use multiple read replicas.
   - **Cache Availability:**
     - Implement multiple cache instances and replicas.
   - **API Gateway Redundancy:**
     - Introduce standby replicas.
   - **Notification Robustness:**
     - Use message brokers (e.g., Kafka, NATS) to ensure message delivery.
   - **Media Storage Cost:**
     - Compress media to save storage space.
   - **Chat Service Overload:**
     - Separate group chat functionality into its own service.

### Key Architecture Design:
- Decouple services for better manageability (User, Chat, Notification, Presence, Media).
- Use WebSockets for real-time messaging.
- Implement caching and media storage to optimize performance.


# Twitter
### System Design for Twitter-like Service

Designing a scalable and efficient Twitter-like system involves addressing both functional and non-functional requirements while ensuring high availability, low latency, and fault tolerance. Below is a step-by-step breakdown of how to achieve this design.

---

## **1. Functional Requirements**

### **Core Features:**
- **Post new tweets:** Users can post text (up to 280 characters) or media (images, videos).
- **Follow users:** Users can follow/unfollow other users, influencing their feed.
- **Newsfeed:** Users see tweets from those they follow in a chronological or ranked order.
- **Search tweets:** Users can search for tweets based on keywords or hashtags.
  
### **Extended Features:**
- **Retweet:** Users can reshare tweets from others.
- **Favorites:** Users can like/favorite tweets.
- **Metrics and analytics:** Collect engagement metrics for user interaction tracking.

---

## **2. Non-Functional Requirements**

### **Scalability:** 
- The system must scale horizontally to handle billions of users and high request throughput (12K RPS).
  
### **Availability:**
- The system must be highly available, with failover mechanisms and redundancy in place.
  
### **Efficiency:** 
- Minimize latency by deploying globally distributed services and using caches.
  
---

## **3. Storage and Traffic Estimations**

### **Daily Traffic:**
- **Total tweets/day:** 1 billion tweets (200M DAU, 5 tweets/user).
- **Media tweets/day:** 100M media files (10% of tweets).
- **RPS:** 12K requests/second.

### **Storage:**
- **Daily storage for tweets:** 100 GB/day for text tweets.
- **Daily storage for media:** 5 TB/day for media (images, videos).
- **10-year storage projection:** ~19 PB.

### **Bandwidth:**
- **Ingress bandwidth:** 60 MB/second for tweet data and media.

---

## **4. High-Level System Design**

### **Core Components:**

1. **User Service:**
   - Handles user registration, login, and profile management.
   - Stores user metadata (usernames, bios, follower/following lists).

2. **Tweet Service:**
   - Manages tweet creation, storage, and retrieval.
   - Supports text and media uploads.

3. **Timeline/Feed Service:**
   - Assembles the user's timeline from tweets posted by followed accounts.
   - This can be **pull-based** (user requests their feed) or **push-based** (real-time updates).

4. **Search Service:**
   - Enables searching for tweets, users, hashtags, etc.
   - Uses an index/search engine like **Elasticsearch** for efficient querying.

5. **Media Service:**
   - Manages the storage and retrieval of media files (images, videos).
   - Stores media in object storage like **Amazon S3** or a similar cloud storage solution.

6. **Notification Service:**
   - Sends real-time notifications for follows, retweets, likes, etc.
   - Integrates with WebSockets or push notifications for mobile users.

---

### **Database Design:**

1. **User Data:**
   - Use a **Relational Database** (e.g., MySQL, Postgres) or **NoSQL Database** (e.g., Cassandra) to store user profiles, follower/following relationships.

2. **Tweets:**
   - Use **NoSQL Databases** (e.g., Cassandra, DynamoDB) for tweet storage due to the high volume and simplicity of storing key-value pairs (tweet ID to tweet content).

3. **Media:**
   - Store media in **object storage** (e.g., S3) with references in the database to manage media associations with tweets.

4. **Search Index:**
   - Use **Elasticsearch** or **Solr** to index and search tweets efficiently.

---

### **Architecture Design:**

1. **API Gateway:**
   - Acts as the front layer for all client requests (tweet posting, feed retrieval, search).
   - Directs requests to appropriate backend services.

2. **Load Balancers:**
   - Distribute traffic evenly among service instances to ensure no single instance is overwhelmed.

3. **Caching Layer:**
   - Use **Redis** or **Memcached** to cache frequent data (e.g., timeline, popular tweets) for low-latency access.

4. **Queueing System:**
   - **Apache Kafka** or **RabbitMQ** for processing events like new tweet posts, retweets, and notifications asynchronously.

---

### **Handling Timelines:**

- **Fanout Write (Push Model):** Every time a user tweets, the system pushes the tweet to the timelines of all followers. This requires more write operations but makes reading timelines very fast.
  
- **Fanout Read (Pull Model):** Tweets are stored individually, and the timeline is assembled when requested. This is more efficient in terms of storage but adds complexity to read operations.

### **Caching Strategies:**

- **Write-through Cache:** Cache the timeline of users as soon as it is generated.
- **Eviction policies:** Use LRU (Least Recently Used) or TTL (Time to Live) to manage cache size.

---

### **Media Storage:**

1. **Media Uploads:**
   - Store media files separately from the main database in distributed object storage like **Amazon S3** or **Google Cloud Storage**.
   - Use a **CDN** (Content Delivery Network) to cache and distribute media files closer to users, reducing load times.

2. **Thumbnailing and Transcoding:**
   - Create thumbnails for images and compressed versions of videos to optimize bandwidth usage.

---

### **Analytics and Monitoring:**

- **Metrics Collection:** Use services like **Prometheus** or **Datadog** to monitor key metrics like tweet rates, RPS, error rates, etc.
  
- **Log Aggregation:** Use **ELK Stack (Elasticsearch, Logstash, Kibana)** for centralized logging and monitoring.

---

## **5. Optimizations**

- **Rate Limiting:** Prevent abuse by rate-limiting requests for users based on IP or account activity.
  
- **Sharding:** Partition large datasets (users, tweets) across multiple servers using sharding techniques (based on user ID or tweet ID).

- **Replication:** Use database replication to ensure high availability and redundancy in case of hardware failures.

---

## **6. Extended Features**

1. **Retweeting:**
   - Store retweets as references to the original tweet. This minimizes data duplication and reduces storage requirements.

2. **Favorites/Likes:**
   - Implement a simple counter system to increment the number of likes on a tweet.

---

## **Conclusion**

This design addresses the high-level requirements of a Twitter-like social media platform, providing a scalable and highly available architecture that can handle billions of users, millions of daily active users, and large-scale media content. By utilizing distributed storage, caching, and efficient database models, the system can meet the performance demands while keeping operational complexity in check.
### Data Model Design Breakdown

The proposed data model reflects the core entities of the Twitter-like application and their relationships. Below is a breakdown of the key tables and their purposes:

---

### **Users Table**

This table stores user information such as name, email, date of birth (DOB), and other user details. Each user is uniquely identified by `userID`.

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `userID`   | UUID      | Unique identifier for each user.           |
| `name`     | String    | User's display name.                       |
| `email`    | String    | User's email address.                      |
| `dob`      | Date      | User's date of birth.                      |
| `bio`      | String    | Optional bio information.                  |
| `profileImageURL` | String | URL of the user's profile image.          |

---

### **Tweets Table**

This table stores all the tweets posted by users, including the type of tweet (text, image, video) and content. Each tweet is associated with the `userID` of the person who posted it.

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `tweetID`  | UUID      | Unique identifier for each tweet.          |
| `userID`   | UUID      | Reference to the user who posted the tweet.|
| `content`  | Text      | The actual content of the tweet.           |
| `mediaURL` | String    | URL of the media file (if any).            |
| `type`     | String    | Type of tweet (text, image, video, etc.).  |
| `createdAt`| Timestamp | Timestamp of when the tweet was created.   |

---

### **Favorites Table**

This table represents the relationship between users and their favorite tweets. It stores references to both the `userID` and `tweetID`.

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `favoriteID` | UUID      | Unique identifier for each favorite entry.|
| `userID`   | UUID      | ID of the user who favorited the tweet.    |
| `tweetID`  | UUID      | ID of the tweet that was favorited.        |
| `favoritedAt`| Timestamp | Timestamp of when the tweet was favorited. |

---

### **Followers Table**

This table handles the many-to-many relationship between users who follow each other. It includes the `followerID` (the user doing the following) and `followeeID` (the user being followed).

| Column       | Data Type | Description                                |
|--------------|-----------|--------------------------------------------|
| `followerID` | UUID      | ID of the user who is following.           |
| `followeeID` | UUID      | ID of the user being followed.             |
| `followedAt` | Timestamp | Timestamp when the follow action occurred. |

---

### **Feeds Table**

This table stores the feed of each user. It includes references to the `userID` and metadata related to the feed, such as how it’s sorted (e.g., chronological or ranked).

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `feedID`   | UUID      | Unique identifier for each feed.           |
| `userID`   | UUID      | Reference to the user whose feed this is.  |
| `lastUpdatedAt`| Timestamp | Last time the feed was updated.          |

---

### **Feeds_Tweets Table**

This table maps tweets to specific feeds, representing the many-to-many relationship between users' feeds and the tweets that appear in them.

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `feedID`   | UUID      | Reference to the feed.                     |
| `tweetID`  | UUID      | Reference to the tweet shown in the feed.  |

---

## **Database Choice**

Given the scale and requirements of this system, we should use a combination of relational and distributed NoSQL databases:

### **Relational Database (PostgreSQL):**
- Suitable for storing structured data like users, followers, and favorites.
- Provides transactional support for operations like following/unfollowing users and adding/removing favorite tweets.

### **NoSQL Database (Cassandra):**
- Ideal for storing high-volume, unstructured data like tweets and feeds.
- Provides scalability, fast write operations, and the ability to handle large datasets distributed across multiple nodes.

**Rationale:**
- Tweets and feeds will require high throughput, low latency, and the ability to scale, making NoSQL (Cassandra) ideal.
- User information and relationships (followers, favorites) benefit from consistency and relational queries, making PostgreSQL a better fit.

---

## **API Design**

### **1. Post a Tweet**

This API allows a user to post a tweet, which could include text and optional media content.

```tsx
postTweet(userID: UUID, content: string, mediaURL?: string): boolean
```

- **Parameters:**
  - `userID` (UUID): Unique identifier of the user posting the tweet.
  - `content` (string): The content of the tweet (text).
  - `mediaURL` (string): Optional URL of the media attached to the tweet (if any).

- **Returns:**
  - `boolean`: True if the tweet is posted successfully, false otherwise.

- **Flow:**
  1. Validate the tweet (e.g., check character limits, sanitize content).
  2. Store the tweet in the `tweets` table (in Cassandra).
  3. If successful, return `true`.

---

### **2. Follow/Unfollow User**

This API allows a user to follow or unfollow another user.

```tsx
follow(followerID: UUID, followeeID: UUID): boolean
unfollow(followerID: UUID, followeeID: UUID): boolean
```

- **Parameters:**
  - `followerID` (UUID): ID of the user initiating the follow/unfollow.
  - `followeeID` (UUID): ID of the user to be followed/unfollowed.

- **Returns:**
  - `boolean`: True if the follow/unfollow action was successful, false otherwise.

- **Flow (Follow):**
  1. Validate that `followerID` and `followeeID` are valid users.
  2. Add an entry in the `followers` table to reflect the relationship.
  3. Update the newsfeed for the `followerID` (push the latest tweets of the followee).
  4. If successful, return `true`.

- **Flow (Unfollow):**
  1. Validate that `followerID` and `followeeID` are valid users.
  2. Remove the entry from the `followers` table.
  3. Update the newsfeed for the `followerID` to remove the followee's tweets.
  4. If successful, return `true`.

---

### **3. Get Newsfeed**

This API retrieves the tweets shown in the user's newsfeed.

```tsx
getNewsfeed(userID: UUID): Tweet[]
```

- **Parameters:**
  - `userID` (UUID): Unique identifier of the user whose newsfeed is requested.

- **Returns:**
  - `Tweet[]`: Array of tweets to be shown in the newsfeed.

- **Flow:**
  1. Fetch the user's feed from the `feeds` table (in Cassandra).
  2. Retrieve the associated tweets using the `feeds_tweets` table.
  3. Return the list of tweets in the desired order (chronological, ranked, etc.).

---

## **Conclusion**

This data model and API design approach offer a scalable solution for handling user tweets, followers, and newsfeeds in a Twitter-like social media application. By using a combination of relational (PostgreSQL) and NoSQL (Cassandra) databases, we ensure that both the structured and unstructured data are handled efficiently at scale.

In the high-level design for the Twitter-like system, you've outlined several critical services and components necessary to scale and optimize functionality. Here's a concise breakdown of the key concepts:


### Designing a URL Shortener

Designing a URL shortener involves creating a system that efficiently handles a large volume of short URL requests and redirections. Here’s a detailed approach to designing such a system.

---

### **Requirements**

#### **Functional Requirements**

1. **Short URL Generation:**
   - Generate a unique, short alias for a given long URL.
   
2. **Redirection:**
   - Redirect users from the short URL to the original long URL.
   
3. **Link Expiration:**
   - Allow URLs to expire after a configurable timespan.

#### **Non-Functional Requirements**

1. **High Availability:**
   - The system should be available 24/7 with minimal downtime.
   
2. **Scalability:**
   - The system should handle increased traffic efficiently, both in terms of read and write operations.

#### **Extended Requirements**

1. **Abuse Prevention:**
   - Implement mechanisms to detect and prevent misuse of the service (e.g., spam or malicious links).
   
2. **Analytics:**
   - Track and record metrics such as the number of times a short URL is accessed.

---

### **Estimation and Constraints**

#### **Traffic Estimation**

- **Reads/Writes per Month:**
  - **Reads:** 10 billion per month
  - **Writes:** 100 million per month

- **Requests Per Second (RPS):**
  - **Writes:** ~40 RPS (100 million requests per month)
  - **Reads (Redirections):** ~4000 RPS (4K URLs/second)

#### **Bandwidth**

- **Incoming Bandwidth:**
  - 20 KB/second for write requests

- **Outgoing Bandwidth:**
  - ~2 MB/second for read requests (assuming each redirection requires 500 bytes of data)

#### **Storage**

- **Total Storage:**
  - 6 TB (for storing 12 billion records over 10 years)

#### **Cache**

- **Daily Cache Needs:**
  - 35 GB/day (caching 20% of the 4K read requests per second)

---

### **System Design Approach**

#### **1. **High-Level Architecture**

1. **Client Requests:**
   - Users send requests to shorten URLs or access short URLs.

2. **API Gateway:**
   - Routes requests to the appropriate service (shortening or redirection).

3. **Shortening Service:**
   - Handles URL shortening logic.
   - Generates unique short codes and stores mappings in the database.

4. **Redirection Service:**
   - Handles redirection requests.
   - Retrieves the original URL from the database using the short code.

5. **Database:**
   - Stores URL mappings, metadata, and expiration information.

6. **Cache:**
   - Caches frequently accessed short URLs to reduce database load.

7. **Analytics Service:**
   - Collects and processes data on URL usage and performance metrics.

8. **Monitoring and Logging:**
   - Monitors system health, performance, and logs errors or anomalies.

#### **2. **Detailed Component Design**

1. **Shortening Algorithm:**
   - **Hashing:** Use hash functions or base62 encoding to generate unique short codes.
   - **Collision Handling:** Implement checks or use a collision-resistant algorithm to ensure uniqueness.

2. **Database Design:**
   - **Schema Example:**
     ```sql
     CREATE TABLE UrlMappings (
         short_url VARCHAR(10) PRIMARY KEY,
         original_url TEXT NOT NULL,
         creation_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
         expiration_date TIMESTAMP
     );
     ```

3. **Caching Strategy:**
   - Use an in-memory cache (e.g., Redis) to store frequently accessed short URL mappings.
   - Implement cache expiration policies to ensure freshness of data.

4. **Redirection Logic:**
   - Efficiently map short URLs to long URLs and handle redirections.
   - Ensure low latency in fetching and redirecting URLs.

5. **Analytics Collection:**
   - Track metrics like click counts, geographical location of users, and timestamp of access.
   - Store aggregated data for reporting and analysis.

6. **Abuse Prevention:**
   - Implement rate limiting, spam detection, and validation checks.
   - Monitor for suspicious activities and take corrective actions.

#### **3. **Scalability and High Availability**

1. **Load Balancing:**
   - Distribute incoming traffic across multiple instances of the shortener and redirection services.

2. **Database Sharding:**
   - Distribute the database across multiple servers to handle large volumes of data and requests.

3. **Replication:**
   - Use database replication to ensure data redundancy and high availability.

4. **Failover Mechanisms:**
   - Implement failover strategies to handle hardware or software failures and maintain service availability.

---

### **Example API Design**

1. **Shorten URL API:**
   ```http
   POST /shorten
   Request Body: {
       "long_url": "https://example.com/very-long-url"
   }
   Response: {
       "short_url": "https://short.ly/abcd1234"
   }
   ```

2. **Redirection API:**
   ```http
   GET /{short_url}
   Response: {
       "redirect_url": "https://example.com/very-long-url"
   }
   ```

---

### **Conclusion**

Designing a URL shortener requires a thoughtful approach to handling high traffic, ensuring scalability, and maintaining system performance. By focusing on key aspects such as URL shortening algorithms, database design, caching, and high availability, you can build a robust and efficient URL shortener service.

### Data Model Design for URL Shortener

#### **Database Schema**

The database schema for the URL shortener can be divided into two main tables:

1. **Users Table:**
   - **Purpose:** Store user details who are creating and managing short URLs.
   - **Columns:**
     - `userID`: Unique identifier for the user (Primary Key).
     - `name`: Name of the user.
     - `email`: Email of the user.
     - `createdAt`: Timestamp when the user was created.

2. **URLs Table:**
   - **Purpose:** Store the details of each short URL.
   - **Columns:**
     - `shortURLID`: Unique identifier for each short URL (Primary Key).
     - `hash`: Short URL identifier (unique, indexed for performance).
     - `originalURL`: The original long URL.
     - `expiration`: Expiration date of the short URL (optional).
     - `userID`: Foreign key linking to the `users` table to identify the creator.

**Schema Example:**

```sql
CREATE TABLE Users (
    userID INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE URLs (
    shortURLID INT AUTO_INCREMENT PRIMARY KEY,
    hash VARCHAR(8) UNIQUE NOT NULL,
    originalURL TEXT NOT NULL,
    expiration TIMESTAMP,
    userID INT,
    FOREIGN KEY (userID) REFERENCES Users(userID)
);
```

#### **Database Choice**

**NoSQL Databases:**

- **Amazon DynamoDB:**
  - **Advantages:** High performance, scalable, fully managed.
  - **Use Case:** Suitable for handling large amounts of data with fast read and write operations.

- **Apache Cassandra:**
  - **Advantages:** Scalable, high availability, distributed database.
  - **Use Case:** Good for applications requiring high write throughput and availability.

- **MongoDB:**
  - **Advantages:** Flexible schema design, high performance.
  - **Use Case:** Ideal for scenarios with evolving data models and high read/write operations.

**SQL Databases:**

- **Azure SQL Database:**
  - **Advantages:** Managed service, good integration with other Azure services.
  - **Use Case:** Suitable if strong relational data consistency is needed.

- **Amazon RDS:**
  - **Advantages:** Managed relational database service, supports multiple SQL database engines.
  - **Use Case:** Good for applications requiring structured data with complex queries.

### API Design for URL Shortener

#### **1. Create URL**

**Description:** Generates a new short URL for a given long URL.

**Endpoint:** `POST /createURL`

**Request Example:**

```json
{
  "apiKey": "your-api-key",
  "originalURL": "https://example.com/very-long-url",
  "expiration": "2024-12-31T23:59:59Z"
}
```

**Response Example:**

```json
{
  "shortURL": "https://short.ly/abcd1234"
}
```

**Parameters:**
- `apiKey` (string): API key for authentication.
- `originalURL` (string): The long URL to shorten.
- `expiration` (Date, optional): When the short URL should expire.

**Returns:**
- `shortURL` (string): The newly created short URL.

#### **2. Get URL**

**Description:** Retrieves the original long URL from a short URL.

**Endpoint:** `GET /getURL`

**Request Example:**

```json
{
  "apiKey": "your-api-key",
  "shortURL": "https://short.ly/abcd1234"
}
```

**Response Example:**

```json
{
  "originalURL": "https://example.com/very-long-url"
}
```

**Parameters:**
- `apiKey` (string): API key for authentication.
- `shortURL` (string): The short URL to look up.

**Returns:**
- `originalURL` (string): The original long URL.

#### **3. Delete URL**

**Description:** Deletes a short URL from the system.

**Endpoint:** `DELETE /deleteURL`

**Request Example:**

```json
{
  "apiKey": "your-api-key",
  "shortURL": "https://short.ly/abcd1234"
}
```

**Response Example:**

```json
{
  "result": true
}
```

**Parameters:**
- `apiKey` (string): API key for authentication.
- `shortURL` (string): The short URL to delete.

**Returns:**
- `result` (boolean): Indicates whether the deletion was successful.

#### **Why Use an API Key?**

An API key:
- **Prevents Abuse:** Limits the number of requests from each user to prevent overuse or misuse.
- **Controls Access:** Helps in identifying and managing users of the service.
- **Rate Limiting:** Allows setting limits on the number of requests per second or minute to protect the service from being overwhelmed.

### Summary

The URL shortener system involves creating and managing a scalable and efficient database to store user and URL data. The API design provides clear endpoints for creating, retrieving, and deleting short URLs while ensuring secure and controlled access through API keys. Choosing the right database (SQL vs NoSQL) depends on the specific requirements and expected data handling needs.
### URL Shortener: Detailed Overview

**Definition:**
A URL shortener is a service that transforms a long URL into a shorter, more manageable one. This short URL redirects users to the original long URL. The primary use cases include simplifying URLs for sharing and tracking link analytics.

### Key Components and Design

#### 1. **URL Encoding**

**Definition:**
URL encoding is the process of converting a long URL into a shorter, unique identifier using an encoding scheme. This helps to ensure that the shortened URL is compact and easy to share.

**Approaches:**

1. **Base62 Encoding:**
   - **Definition:** Base62 encoding uses 62 characters (A-Z, a-z, 0-9) to represent numbers. This allows for a large number of unique short URLs.
   - **Advantages:**
     - Simple and easy to implement.
     - Scales well with the number of characters used.
   - **Disadvantages:**
     - Doesn't guarantee uniqueness; collisions can occur.
     - Limited by the length of the generated key.

2. **MD5 Hashing:**
   - **Definition:** MD5 is a hash function that produces a 128-bit hash value, which can be converted to a shorter URL. MD5 is widely used for hashing data.
   - **Advantages:**
     - Produces a fixed-length output, regardless of input size.
   - **Disadvantages:**
     - Hash collisions can occur, leading to duplicate short URLs.
     - Computational overhead and potential security vulnerabilities (MD5 is not cryptographically secure).

3. **Counter-Based Approach:**
   - **Definition:** A counter-based approach uses an incrementing counter to generate unique IDs for URLs. These IDs are then encoded into a short URL.
   - **Advantages:**
     - Ensures uniqueness as long as the counter is properly managed.
   - **Disadvantages:**
     - Can become a single point of failure.
     - Requires a distributed counter to handle high traffic and avoid collisions.

#### 2. **Key Generation Service (KGS)**

**Definition:**
A Key Generation Service is responsible for creating unique keys used in short URLs. It ensures that each key is unique and manages key assignment.

**Advantages:**
- Centralizes key generation and management.
- Reduces the risk of key duplication.

**Disadvantages:**
- Can become a bottleneck if not properly scaled.
- Needs to handle high concurrency and prevent race conditions.

#### 3. **Caching**

**Definition:**
Caching involves storing frequently accessed data in memory to reduce latency and improve response times. In the context of URL shorteners, caching helps to quickly resolve short URLs to their original counterparts.

**Advantages:**
- Reduces database load and improves performance.
- Provides faster access to frequently requested data.

**Disadvantages:**
- Adds complexity to the system.
- Cache invalidation and consistency need to be managed carefully.

#### 4. **High-Level System Design**

**Components:**

1. **API Server:**
   - **Role:** Handles incoming requests for creating, retrieving, and deleting URLs.
   - **Advantages:** Centralized point for handling user interactions.
   - **Disadvantages:** Needs to be highly scalable to handle high traffic.

2. **Database:**
   - **Role:** Stores the mappings between short URLs and original URLs, as well as user data.
   - **Advantages:** Persistent storage for URLs and user information.
   - **Disadvantages:** Database performance and scalability can be challenging with high traffic.

3. **Key Generation Service (KGS):**
   - **Role:** Generates unique keys for short URLs.
   - **Advantages:** Ensures uniqueness and avoids collisions.
   - **Disadvantages:** Requires robust management to handle high demand.

4. **Cache:**
   - **Role:** Stores frequently accessed URL mappings to reduce latency.
   - **Advantages:** Improves performance by reducing database load.
   - **Disadvantages:** Needs to be managed to ensure data consistency.

**Workflow:**

1. **Creating a Short URL:**
   - User requests a short URL for a long URL.
   - API server requests a unique key from KGS.
   - KGS provides a key, which is used to create a short URL.
   - The short URL and its mapping are stored in the database and cache.

2. **Accessing a Short URL:**
   - User accesses a short URL.
   - API server checks the cache for the URL mapping.
   - If not found in the cache, the server retrieves it from the database.
   - The user is redirected to the original URL or receives a 404 error if the URL is not found.

**Advantages:**
- Simplifies long URLs for easier sharing and tracking.
- Provides analytics and metrics for URL usage.

**Disadvantages:**
- Potential for abuse and misuse (e.g., spamming).
- Requires ongoing maintenance and scaling to handle traffic and data growth.

This detailed breakdown covers the core concepts, advantages, and disadvantages of designing and implementing a URL shortener. If you need more specific details or have further questions, feel free to ask!

### Detailed Design of URL Shortener

In this detailed design overview, we’ll cover advanced aspects of the URL shortener system, including data partitioning, database cleanup strategies, caching mechanisms, metrics and analytics, and security considerations. We'll also discuss how to identify and resolve bottlenecks to ensure a robust and scalable system.

#### 1. **Data Partitioning**

**Definition:**
Data partitioning (or sharding) involves dividing a database into smaller, more manageable pieces. This helps in scaling out the system by distributing data across multiple servers or nodes.

**Partitioning Schemes:**

- **Hash-Based Partitioning:**
  - **Definition:** Data is distributed across partitions based on a hash function applied to a key (e.g., user ID).
  - **Advantages:** Even distribution of data; straightforward implementation.
  - **Disadvantages:** Rebalancing can be complex if partitions need to be added or removed.

- **List-Based Partitioning:**
  - **Definition:** Data is distributed based on predefined ranges or lists (e.g., user regions).
  - **Advantages:** Simple for cases with clear categorical distributions.
  - **Disadvantages:** May lead to uneven data distribution if the list items have skewed data sizes.

- **Range-Based Partitioning:**
  - **Definition:** Data is divided based on ranges of values (e.g., timestamp ranges).
  - **Advantages:** Useful for time-series data; efficient for range queries.
  - **Disadvantages:** May lead to uneven partitions if data distribution is not uniform.

- **Composite Partitioning:**
  - **Definition:** Combines multiple partitioning schemes, such as hash and range.
  - **Advantages:** More flexible and can address multiple use cases.
  - **Disadvantages:** More complex to implement and manage.

- **Consistent Hashing:**
  - **Definition:** A technique to distribute data across a cluster of nodes in a way that minimizes reorganization when nodes are added or removed.
  - **Advantages:** Reduces rebalancing overhead and improves load distribution.
  - **Disadvantages:** Complexity in implementation and management.

#### 2. **Database Cleanup**

**Definition:**
Database cleanup involves removing expired or outdated entries from the database to maintain performance and manage storage.

- **Active Cleanup:**
  - **Definition:** A separate cleanup service periodically removes expired entries.
  - **Advantages:** Ensures timely removal of obsolete data; predictable cleanup intervals.
  - **Disadvantages:** Additional processing overhead; requires scheduling and maintenance.

- **Passive Cleanup:**
  - **Definition:** Entries are removed upon access if they are found to be expired.
  - **Advantages:** Lazy approach that reduces processing overhead.
  - **Disadvantages:** Expired entries might remain in the database longer; less predictable.

#### 3. **Cache**

**Definition:**
Caching stores frequently accessed data in memory to speed up retrieval and reduce load on the database.

- **Cache Eviction Policy:**
  - **Least Recently Used (LRU):**
    - **Definition:** Removes the least recently accessed items first.
    - **Advantages:** Simple and effective for scenarios where recent items are likely to be accessed again.
    - **Disadvantages:** May not always reflect actual data usage patterns; can be complex to implement with large data sets.

- **Handling Cache Misses:**
  - **Definition:** When data is not found in the cache, it’s fetched from the database and then added to the cache.
  - **Advantages:** Ensures that cache remains updated with frequently accessed data.
  - **Disadvantages:** Increased load on the database; potential for cache staleness.

#### 4. **Metrics and Analytics**

**Definition:**
Metrics and analytics involve collecting and analyzing data related to URL usage, such as access counts, user demographics, and performance.

- **Advantages:**
  - Provides insights into user behavior and system performance.
  - Helps in optimizing the system and making data-driven decisions.

- **Disadvantages:**
  - Requires additional storage and processing.
  - Ensuring data privacy and security can be complex.

#### 5. **Security**

**Definition:**
Security measures protect the URL shortener service from unauthorized access and misuse.

- **Private URLs and Authorization:**
  - **Definition:** Restrict access to URLs based on user permissions.
  - **Advantages:** Enhances security and controls access.
  - **Disadvantages:** Adds complexity to the system; requires user authentication mechanisms.

- **API Gateway:**
  - **Definition:** A service that handles routing, authorization, and rate limiting for APIs.
  - **Advantages:** Simplifies API management; provides built-in security features.
  - **Disadvantages:** Can become a single point of failure; additional cost and complexity.

#### 6. **Identifying and Resolving Bottlenecks**

**Potential Bottlenecks:**

- **API Service or Key Generation Service Crashes:**
  - **Solution:** Deploy multiple instances of these services and use load balancers to distribute traffic.

- **Traffic Distribution:**
  - **Solution:** Implement load balancers to distribute requests evenly across servers and services.

- **Database Load:**
  - **Solution:** Use read replicas to handle read-heavy operations; optimize queries and indexing.

- **Key Database Failure:**
  - **Solution:** Implement a standby replica for failover and ensure high availability.

- **Cache Availability:**
  - **Solution:** Use multiple instances and replicas of the cache to ensure redundancy and high availability.

**Advanced Design Overview:**

1. **Multiple Instances and Load Balancers:**
   - **Definition:** Deploy multiple instances of servers and use load balancers to manage traffic.
   - **Advantages:** Enhances scalability and fault tolerance.
   - **Disadvantages:** Increased complexity in managing and configuring multiple instances.

2. **Read Replicas for Database:**
   - **Definition:** Use read replicas to handle read operations separately from write operations.
   - **Advantages:** Improves read performance and reduces load on the primary database.
   - **Disadvantages:** Requires synchronization between replicas and primary database.

3. **Distributed Cache Instances:**
   - **Definition:** Implement multiple instances and replicas of the cache to ensure availability and performance.
   - **Advantages:** Provides redundancy and improves cache performance.
   - **Disadvantages:** Adds complexity in managing cache consistency and replication.

This detailed design covers the critical aspects of building and maintaining a scalable and robust URL shortener system. Understanding and addressing these components will help in creating a system that is both efficient and resilient.




### **1. Design a Real-Time Chat Application (e.g., WhatsApp, Slack)**

- **Key Focus Areas:**
  - Message delivery mechanisms (push/pull)
  - Handling online/offline users
  - Ensuring message ordering and delivery guarantees
  - Scaling to millions of concurrent users
  - Data storage for message history
  - Security considerations (encryption, authentication)

### **2. Design a Real-Time Collaborative Document Editing Service (e.g., Google Docs)**

- **Key Focus Areas:**
  - Concurrency control and conflict resolution
  - Real-time synchronization across clients
  - Data consistency models
  - Operational transformation or conflict-free replicated data types (CRDTs)
  - Scalability and fault tolerance

### **3. Design a Ride-Sharing Service (e.g., Uber, Lyft)**

- **Key Focus Areas:**
  - Real-time matching of riders and drivers
  - Geo-spatial indexing and querying
  - Route optimization
  - Surge pricing algorithms
  - Handling high traffic in specific regions
  - Data consistency and eventual consistency models

### **4. Design a Real-Time Bidding System for Online Advertising**

- **Key Focus Areas:**
  - Low-latency bid processing
  - Handling high throughput of bid requests
  - Auction algorithms (first-price, second-price auctions)
  - Advertiser budget management
  - Click-through rate (CTR) prediction
  - Fraud detection mechanisms

### **5. Design a Stock Trading Platform**

- **Key Focus Areas:**
  - Real-time market data processing
  - Order matching engine
  - Transaction processing with ACID properties
  - Latency optimization
  - Risk management and compliance
  - Data storage and retrieval for trade history

### **6. Design a Monitoring and Alerting System (e.g., Prometheus, Nagios)**

- **Key Focus Areas:**
  - Real-time data collection from various sources
  - Time-series data storage
  - Threshold-based and anomaly detection alerting
  - Dashboard design for data visualization
  - Scalability to handle large volumes of metrics
  - High availability and fault tolerance

### **7. Design a Real-Time Analytics Platform**

- **Key Focus Areas:**
  - Stream processing frameworks (e.g., Apache Kafka, Flink)
  - Data ingestion and ETL pipelines
  - Handling data velocity and volume
  - Windowing and aggregation techniques
  - Consistency and state management
  - Integration with data storage systems

### **8. Design a Content Delivery Network (CDN)**

- **Key Focus Areas:**
  - Distributed caching strategies
  - Content replication and invalidation
  - Load balancing across edge servers
  - Handling dynamic and static content
  - Network latency optimization
  - Security (DDoS protection, SSL termination)

### **9. Design a Multiplayer Online Gaming Platform**

- **Key Focus Areas:**
  - Real-time state synchronization between players
  - Latency minimization techniques
  - Event handling and game loop architecture
  - Cheat prevention and security
  - Scalability for concurrent users
  - Matchmaking algorithms

### **10. Design a Notification System**

- **Key Focus Areas:**
  - Message queuing and processing
  - Push notification services (APNs, FCM)
  - Real-time delivery guarantees
  - User preferences and opt-in mechanisms
  - Throttling and rate limiting
  - Monitoring and analytics

### **11. Design a Real-Time Search Autocomplete Feature**

- **Key Focus Areas:**
  - Efficient data structures (tries, prefix trees)
  - Low-latency query processing
  - Handling misspellings and suggestions
  - Ranking algorithms based on popularity or personalization
  - Scaling to support numerous queries per second
  - Caching strategies

### **12. Design a Live Video Streaming Service (e.g., Twitch, YouTube Live)**

- **Key Focus Areas:**
  - Video encoding and transcoding
  - Real-time content distribution
  - Handling high bandwidth requirements
  - Latency between broadcaster and viewers
  - Chat and interaction features
  - Content delivery optimization

### **13. Design a Distributed Cache System**

- **Key Focus Areas:**
  - Data partitioning and sharding
  - Consistency models (strong vs. eventual)
  - Cache invalidation strategies
  - Replication and high availability
  - Dealing with cache misses and fallbacks
  - Scalability and performance optimization

### **14. Design a Real-Time Recommendation Engine**

- **Key Focus Areas:**
  - User behavior tracking
  - Collaborative filtering and content-based filtering
  - Real-time data processing and model updates
  - Personalization techniques
  - Scalability for large user bases
  - A/B testing frameworks

### **15. Design a High-Frequency Trading System**

- **Key Focus Areas:**
  - Ultra-low latency processing
  - Direct market access protocols
  - Risk management and compliance
  - Co-location strategies
  - Real-time data feeds and processing
  - Fault tolerance mechanisms

---

## **General Preparation Tips**

- **Understand Core Concepts:**
  - Familiarize yourself with networking protocols, database systems, caching mechanisms, and message queues.
- **Scalability and Performance:**
  - Be prepared to discuss how to scale systems horizontally and vertically.
  - Know how to identify and mitigate bottlenecks.
- **Data Consistency and Integrity:**
  - Understand different consistency models and where to apply them.
- **Trade-offs:**
  - Be ready to discuss the trade-offs between latency, throughput, consistency, and availability.
- **Security Considerations:**
  - Highlight how to secure data in transit and at rest.
- **Monitoring and Maintenance:**
  - Discuss strategies for logging, monitoring, and alerting.
- **Fault Tolerance and Reliability:**
  - Explain how to design systems that can gracefully handle failures.
- **APIs and Integration:**
  - Understand how different components communicate and integrate with external services.
- **Latest Technologies:**
  - Stay updated with the latest tools and frameworks relevant to real-time systems (e.g., Kafka, Redis, Kubernetes).

---

## **Effective Communication During the Interview**

- **Clarify Requirements:**
  - Ask questions to ensure you understand the problem scope.
- **Think Aloud:**
  - Share your thought process with the interviewer.
- **Structured Approach:**
  - Start with a high-level design before diving into details.
- **Use Diagrams:**
  - Draw diagrams to illustrate your design (components, data flow, etc.).
- **Consider Edge Cases:**
  - Discuss how your design handles failures, peak loads, and other edge cases.
- **Be Open to Feedback:**
  - Be prepared to adjust your design based on the interviewer's hints or suggestions.

---

### **1. Design a Real-Time Chat Application**
**Architecture:**
- **Backend Services:** Utilize WebSocket for maintaining a persistent, full-duplex communication channel that allows for real-time data flow.
- **Database:** Use NoSQL databases like Cassandra for scalable message storage and fast retrieval.
- **Message Queue:** Implement RabbitMQ or Kafka to handle high-throughput message delivery, ensuring durability and fault tolerance.
- **Caching:** Deploy Redis to cache frequent queries and active data, reducing load on the database.
- **Security:** Implement TLS/SSL for data transmission and at-rest encryption for stored messages.

### **2. Design a Real-Time Collaborative Document Editing Service**
**Architecture:**
- **Operational Transformation (OT) or CRDTs:** Use these algorithms to handle concurrent modifications and ensure data consistency without conflicts.
- **Backend Synchronization:** Utilize WebSockets to sync data in real-time between clients and servers.
- **Data Storage:** Consider a combination of document-based storage solutions like MongoDB and a caching layer with Redis to handle frequent access and modifications.
- **Revision Control:** Implement a version control system to track changes and revert to previous states if needed.

### **3. Design a Ride-Sharing Service**
**Architecture:**
- **Geo-distributed Database:** Use databases like Google Cloud Spanner or geo-partitioned tables in CockroachDB to manage geo-spatial data efficiently.
- **Matching Algorithm:** Implement efficient matching algorithms that run on scalable compute clusters to minimize wait time and optimize ridesharing.
- **Real-Time Notifications:** Use push notifications via Firebase or a custom WebSocket implementation to update users about ride status.

### **4. Design a Real-Time Bidding System for Online Advertising**
**Architecture:**
- **High-Performance Computing:** Utilize in-memory databases like Aerospike for low-latency bid processing.
- **Stream Processing:** Kafka Streams or Apache Flink for handling real-time bid stream analysis and decision-making.
- **Budget Tracking:** Use distributed counters in Redis or CRDTs to manage advertiser budgets in real-time.

### **5. Design a Stock Trading Platform**
**Architecture:**
- **Order Matching Engine:** Build a low-latency, high-throughput system using custom algorithms that can process and match orders in microseconds.
- **Data Feed Handling:** Implement message brokers like Kafka for handling real-time market data feeds efficiently.
- **Data Storage:** Use time-series databases like InfluxDB for storing trade history and tick data.

### **6. Design a Monitoring and Alerting System**
**Architecture:**
- **Data Collection:** Use agents like Telegraf to collect metrics and logs from various sources.
- **Time-Series Database:** Store metrics in Prometheus or InfluxDB, which are optimized for time-series data.
- **Alerting:** Use tools like Grafana or a custom service that evaluates conditions and sends notifications via email, SMS, or webhooks.

### **7. Design a Real-Time Analytics Platform**
**Architecture:**
- **Stream Processing:** Utilize Kafka coupled with Apache Flink or Spark Streaming for real-time data processing and aggregation.
- **Data Lake:** Use Apache Hadoop or cloud solutions like AWS S3 to store raw data for batch processing and historical analysis.
- **Query Engine:** Deploy Apache Druid for real-time queries on aggregated data.

### **8. Design a Content Delivery Network (CDN)**
**Architecture:**
- **Edge Caching:** Deploy multiple edge locations that cache content closer to users to reduce latency.
- **Content Management:** Use a centralized management system to handle invalidation and distribution logic.
- **Load Balancing:** Implement DNS-based load balancing techniques to direct requests to the nearest edge server.

### **9. Design a Multiplayer Online Gaming Platform**
**Architecture:**
- **Game State Synchronization:** Use reliable UDP (e.g., QUIC) to minimize latency in state transmission.
- **Matchmaking Service:** Implement scalable matchmaking services that can handle thousands of concurrent matchmaking requests.
- **Cheat Detection:** Integrate anti-cheat engines that monitor gameplay for anomalies.

### **10. Design a Notification System**
**Architecture:**
- **Message Queue:** Kafka or RabbitMQ to manage the flow of messages and ensure reliable delivery.
- **Worker Nodes:** Deploy multiple worker nodes that process notifications and handle retries and failures.
- **Rate Limiting:** Implement rate-limiting mechanisms to control the flow of outbound messages and prevent system overload.

### **11. Design a Real-Time Search Autocomplete Feature**
**Architecture:**
- **Trie Data Structure:** Implement a trie to store possible search terms efficiently, enabling quick prefix searches.
- **Caching:** Use Redis to cache popular queries and results to reduce latency.
- **Backend API:** Build a lightweight API layer that handles search queries and interacts with the trie and cache.

### **12. Design a Live Video Streaming Service**
**Architecture:**
- **Streaming Protocol:** Use protocols like HLS or DASH for adaptive bitrate streaming, which adjusts video quality based on user bandwidth.
- **Edge Caching:** Implement CDN solutions to distribute and cache video content.
- **Interaction Layer:** Use WebSockets for real-time chat and interaction features among viewers.

### **13. Design a Distributed Cache System**
**Architecture:**
- **Data Sharding:** Shard data across multiple nodes to distribute load and increase availability.
- **Replication:** Implement master-slave replication to provide redundancy and improve fault tolerance.
- **Consistency:** Use consistency protocols like quorum or read-repair to maintain cache coherence.

### **14. Design a Real-Time Recommendation Engine**
**Architecture:**
- **Machine Learning Pipelines:** Build real-time data processing pipelines using Kafka and Spark ML to update recommendation models.
- **User Profile Store:** Use a scalable NoSQL database like Cassandra to store user profiles and behavior.
- **API Layer:** Develop APIs that deliver personalized recommendations based on the latest models and user interactions.

### **15. Design a High-Frequency Trading System**
**Architecture:**
- **Low-Latency Networking:** Implement network protocols and hardware that minimize latency for trade execution.
- **Data Processing:** Use specialized algorithms and hardware (e.g., FPGA) for ultra-fast order matching.
- **Risk Management:** Integrate real-time risk analysis tools to monitor and manage potential trading risks.

