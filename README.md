# CDR Microservices Project

This repository contains a **Call Detail Record (CDR) System** built with a microservices architecture.  
It aggregates three services as **submodules** and orchestrates them with Docker Compose.

The project showcases the use of **Spring Boot, Java, Python, Kafka, PostgreSQL, and Docker Compose** in building scalable backend systems.

---

## Microservices
- **Cdr-Generator** → Produces synthetic CDR data and sends it to Kafka.  
- **Cdr-Processor** → Consumes CDR messages from Kafka, processes them, and stores in PostgreSQL.  
- **Cdr-Reporter** → Provides REST API endpoints to query stored CDR data.  

---

## Getting Started

### 1. Clone the Repository
Make sure to include submodules:
```bash
git clone --recurse-submodules https://github.com/bsinemcetiner/Cdr-Microservices.git
cd Cdr-Microservices
```
If you already cloned without submodules, run:
```bash
git submodule update --init --recursive
```

### 2. Run with Docker Compose
Bring up the full system (Zookeeper, Kafka, PostgreSQL, and all 3 services):
```bash
docker-compose up --build
```

_-Generator will start producing fake CDRs into Kafka._

_-Processor will consume and store them into PostgreSQL._

_-Reporter exposes REST APIs_


### 3. Interacting with the API (Swagger / Postman)

The application runs at:  
- [http://localhost:8080/api/cdrs](http://localhost:8080/api/cdrs)

You can interact with the REST API using:

-  **Swagger UI** → [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)
-  **Postman**

---

## Tech Stack
- **Java (Spring Boot)** → Processor & Reporter  
- **Python** → Generator  
- **PostgreSQL** → Database  
- **Apache Kafka + Zookeeper** → Messaging backbone  
- **Docker & Docker Compose** → Container orchestration  

---

## Repository Structure
**Cdr-Microservices**
- _Cdr-Generator:_ Python service to generate CDRs

- _Cdr-Processor:_ Java service to consume & process
  
- _Cdr-Reporter:_ Java service to expose APIs
  
- _docker-compose.yml:_ Compose file to run the full system

---

## Notes

Make sure Docker and Docker Compose are installed.

For viewing logs:
```bash
docker logs -f <container_name>
```

Stop all services:
```bash
docker-compose down
```


