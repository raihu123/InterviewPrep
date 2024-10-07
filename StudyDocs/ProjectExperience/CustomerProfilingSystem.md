**Project Architecture Overview**

The project involved a comprehensive transformation of an outdated Service-Oriented Architecture (SOA)-based application into a modern microservices architecture. The main objectives were to enhance system scalability, improve maintainability, and reduce operational costs. This was achieved by leveraging a suite of contemporary technologies and best practices.

---

**Technologies Used and Their Purpose** : Java, Spring, Angular, Oracle, Kafka & Alfresco

1. **Java and Spring Framework**
   - **Why Used**: The development of scalable microservices.
   - **Application in Project**: Utilized for developing independent microservices that encapsulate specific business functionalities, allowing for modular development and easier maintenance.

2. **Angular**
   - **Why Used**: Angular for front-end web application framework 
   - **Application in Project**: communicates with back-end services via RESTful APIs

3. **Oracle Database (Oracle/PLSQL)**
   - **Why Used**: Oracle Database ifor reliability and scalability in large volumes of data, making it suitable for enterprise-level applications.
   - **Application in Project**: Optimized existing database queries and procedures to reduce latency by 20%, leading to faster data retrieval and improved application performance.

4. **Apache Kafka**
   - **Why Used**: Kafka is a distributed async platform capable of high throughput and low latency.
   - **Application in Project**: Implemented for asynchronous communication between microservices, enabling real-time data processing and decoupling services to enhance scalability.

5. **Alfresco for Document Management**
   - **Why Used**: Alfresco is an open-source enterprise content management system 
   - **Application in Project**: Replaced a 9TB legacy file system, automating 80% of manual document handling tasks, thereby reducing manual labor and operational costs.

---

```text
+------------------------+
|      Front-End         |
|       (Angular)        |
+-----------+------------+
            |
            v
+------------------------+
|     API Gateway with   |
|   Integrated Circuit   |
|        Breaker         |
+-----------+------------+
            |
            v
   +--------+--------+
   |                 |
   v                 v
+------+         +-------+
|Customer Profile|       |
| Registration   |       |
|    System      |       |
+---+--+         |Customer|
    |  |         | Profile|
    |  |         |Document|
    |  |         |Generator|
    |  |         +----+----+
    |  |              |
    v  v              v
+---------+       +---------+
| Oracle  |       | Alfresco|
|Database |       |Document |
+---------+       |Management|
                  |  System  |
                  +---------+
```

**Architectural Transformation**

- **From SOA to Microservices**
  - **Rationale**: The existing SOA-based system was monolithic, making it difficult to scale and maintain. Transitioning to microservices allows for independent deployment, scaling, and development of services.
  - **Implementation**: Decomposed the monolithic application into smaller, independent microservices using Java and Spring. Each microservice handles a specific business function and communicates with others through well-defined APIs.

- **Automation and Legacy System Elimination**
  - **Rationale**: Manual jobs were time-consuming and error-prone. Automating these tasks increases efficiency and accuracy.
  - **Implementation**: Leveraged Java, Spring, APIs, and Kafka to automate workflows, which led to the decommissioning of a massive 9TB legacy file system.

- **Database Optimization**
  - **Rationale**: High latency in database operations was affecting application performance.
  - **Implementation**: Optimized SQL queries and PLSQL procedures in the Oracle database, reducing latency by 20% and enhancing overall system responsiveness.

---

**Potential Challenges and Mitigation Strategies**

**Inter-Service Communication**
 - **Challenge**: Latency and reliability in communication between services.
 - **Mitigation**: Utilize asynchronous messaging systems like Kafka and implement retries and circuit breakers to handle failures.

**Legacy System Integration**
 - **Challenge**: Ensuring new microservices work seamlessly with remaining legacy systems.
 - **Mitigation**: Implement APIs or middleware to bridge between old and new systems, and plan for gradual phase-out of legacy components.

**Team Coordination**
 - **Challenge**: Increased need for collaboration among teams working on different services.
 - **Mitigation**: Foster a DevOps culture, encouraging continuous integration and continuous deployment (CI/CD) practices.

**Performance Overheads**
 - **Challenge**: Network overhead due to inter-service calls can degrade performance.
 - **Mitigation**: Optimize service endpoints, use load balancing, and implement caching mechanisms where appropriate.



### **Challenge: Data Inconsistency in Customer Profiling Microservices**

**Context:**

Our application included several microservices responsible for different aspects of customer profiling:

1. **Customer Service**: Manages basic customer information.
2. **Profile Service**: Handles customer profiles, preferences, and settings.
3. **Notification Service**: Sends out confirmation emails and notifications.
4. **Account Service**: Manages account-related data, such as credentials and security settings.

These services needed to work in harmony to ensure that when a customer profile is created or updated, all related data across the services remain consistent.

---

**Step-by-Step Explanation of the Data Inconsistency Issue:**

1. **Initiating a Profile Update:**
   - A customer requests to update their profile information via the Angular front-end application.
   - The request is sent to the **Profile Service** to update preferences and settings.

2. **Distributed Transaction Begins:**
   - The **Profile Service** initiates a distributed transaction using the Saga pattern.
   - The transaction involves the **Customer Service**, **Account Service**, and **Notification Service**.

3. **Service Execution Order:**
   - **Step 1**: **Profile Service** updates the profile data in its own database.
   - **Step 2**: **Customer Service** updates basic customer information.
   - **Step 3**: **Account Service** updates account security settings.
   - **Step 4**: **Notification Service** sends a confirmation email.

4. **Failure Occurs:**
   - Suppose the **Account Service** encounters a database timeout and fails to update the account security settings.
   - Since the Saga pattern is used, compensating transactions need to be executed to roll back the previous steps.

5. **Compensating Transactions Fail:**
   - The **Profile Service** attempts to roll back its update but fails due to a network issue.
   - Now, the **Customer Service** data remains updated, but the **Profile Service** and **Account Service** are out of sync.

6. **Resulting Data Inconsistency:**
   - The customer profile shows outdated preferences, but the basic customer information is updated.
   - Notifications may be sent with incorrect data, leading to confusion and a poor user experience.

---

### **Mitigation Strategy: Resolving the Data Inconsistency Issue**

**Step-by-Step Solution:**

1. **Implement Idempotent Operations:**
   - Ensure that all service operations are idempotent, meaning that repeating the same operation produces the same result without adverse effects.
   - This allows safe retries of failed operations.

2. **Enhance Saga Coordination:**
   - Use a more robust Saga orchestrator that can handle partial failures and retries.
   - Implement timeouts and circuit breakers to prevent long waits and cascading failures.

3. **Introduce a Distributed Transaction Log:**
   - Maintain a transaction log that records the state of each step in the Saga.
   - This log helps in auditing and retrying failed steps accurately.

4. **Use Eventual Consistency and Retries:**
   - Accept that immediate consistency may not be achievable.
   - Design the system for eventual consistency, where data will become consistent after some time.
   - Implement automatic retries for failed compensating transactions.

5. **Implement Dead Letter Queues in Kafka:**
   - Messages that cannot be processed are sent to a dead letter queue.
   - Set up monitoring to handle these messages manually or trigger alerts.

6. **Improve Error Handling and Notifications:**
   - Enhance error handling to catch exceptions and provide meaningful feedback.
   - Notify administrators when critical failures occur so they can intervene promptly.

7. **Test Failure Scenarios Extensively:**
   - Perform chaos testing to simulate failures in different services.
   - Ensure that the system can recover gracefully from various failure modes.

8. **Data Reconciliation Processes:**
   - Schedule regular data reconciliation jobs that compare data across services.
   - Automatically correct inconsistencies detected during these reconciliations.

---

**Implementation of the Mitigation:**

- **Enhanced Saga Orchestrator:**
  - We upgraded our Saga orchestrator to include better failure handling mechanisms.
  - The orchestrator was configured to retry failed steps a limited number of times before marking the transaction as failed.

- **Idempotency and Retries:**
  - All service endpoints were redesigned to be idempotent.
  - Implemented retry logic with exponential backoff to handle transient failures.

- **Eventual Consistency:**
  - Adopted an eventual consistency model, accepting that some data might not be immediately consistent.
  - Leveraged Apache Kafka to publish events that other services subscribe to, ensuring they eventually receive and process updates.

- **Distributed Transaction Log:**
  - Created a centralized transaction log stored in a resilient data store.
  - This log tracks the state of each transaction and aids in recovery and auditing.

- **Monitoring and Alerts:**
  - Set up monitoring tools (like Prometheus and Grafana) to track the health of microservices.
  - Configured alerts to notify the team when anomalies occur, such as repeated transaction failures.

- **Data Reconciliation:**
  - Developed scripts that run during off-peak hours to check for data inconsistencies.
  - Implemented automated fixes where possible and flagged issues requiring manual intervention.

---

### **Conclusion**

By addressing the data inconsistency issue step by step, we improved the reliability and robustness of our customer profiling system. Implementing the Saga pattern with enhanced coordination and adopting an eventual consistency model allowed us to handle distributed transactions more effectively. Regular monitoring and data reconciliation ensured that any inconsistencies were promptly detected and resolved, maintaining the integrity of customer data across all services.

---

**Key Takeaways:**

- **Understanding the Challenge:**
  - Data consistency in microservices is complex due to distributed nature and potential failures.
  - Implementing patterns like Saga requires careful consideration of failure scenarios.

- **Mitigation Strategies:**
  - Idempotency and retries are crucial for handling transient failures.
  - Eventual consistency models can be more practical than immediate consistency in distributed systems.
  - Robust monitoring and alerting systems are essential for timely detection of issues.

- **Importance of Testing:**
  - Simulating failures through chaos testing helps in preparing the system to handle real-world issues.
  - Regular data reconciliation helps in maintaining data integrity over time.

By proactively addressing these challenges, we ensured that our microservices-based application provided a reliable and consistent customer profiling experience, even in the face of complex distributed transactions.