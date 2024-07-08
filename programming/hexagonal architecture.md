---
tags:
  - hexagonal
  - concept
  - architecture
---

The Hexagonal Architecture, also known as the Ports and Adapters Architecture, is an approach to designing and organizing code based on the primary design principle of separation of concerns. It focuses on decoupling the business logic from external dependencies on any technology or framework by organizing code into separate layers.

In the context of the Adapter and Handler patterns within the structure of the Hexagonal Architecture, a port serves as an interface that defines the methods used by adapters to establish connections with the core of the application. There are two types of ports in this architecture: driving ports and driven ports.

- **Driving Ports:** These ports facilitate the connection between the driving adapter and the use case application. They are responsible for handling inputs from external sources.
    
- **Driven Ports:** Driven ports establish connections between use cases and other adapters within different hexagons, enabling communication between various parts of the application.