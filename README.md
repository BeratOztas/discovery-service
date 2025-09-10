# discovery-service (Eureka Server)

This is the central service discovery server for the Gym CRM microservice ecosystem. It uses **Spring Cloud Eureka** to provide a registry where all other microservices can register themselves and discover each other dynamically.

## Features

- **Service Registry:** Acts as a central "address book" for all microservices. When a microservice starts, it registers its location (host and port) with this server.
- **Service Discovery:** Allows client-side microservices to query the registry to find the locations of other services they need to communicate with.
- **Fault Tolerance:** Built for resilience, it provides peer-to-peer replication to ensure high availability.
- **REST API:** Exposes a simple RESTful API for registration and discovery, managed automatically by Spring Cloud.
- **Self-Preservation Mode:** Prevents mass de-registrations during network partitions, improving stability.

## Technologies

- **Java 17+**
- **Spring Boot**
- **Spring Cloud Netflix (for Eureka)**

---

## How to Run

The `discovery-service` must be the first service to be started in the entire microservice ecosystem. All other services depend on it to register and find each other.

**Run Order:**

1.  **`discovery-service`**: Start the Eureka Server first.
2.  **Other Microservices**: Start the other microservices (`gym-crm`, `trainer-hours-service`, etc.). They will register themselves with this server.