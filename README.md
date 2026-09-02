# 🏥 Hospital Server - Service Registry (Netflix Eureka)

[![Spring Boot](https://img.shields.io/badge/Spring--Boot-3.x-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Spring Cloud Netflix](https://img.shields.io/badge/Eureka-Server-yellow.svg)](https://spring.io/projects/spring-cloud-netflix)
[![Architecture](https://img.shields.io/badge/Microservice-Registry-blue.svg)](https://microservices.io/patterns/service-registry.html)

**Hospital Server** is the **Service Discovery and Registry Server** for the **Hospital Management System (HMS)** microservices platform. Powered by Spring Cloud Netflix Eureka Server, it enables client-side load balancing, dynamic service registration, health monitoring, and seamless inter-service communication without hardcoded IP addresses or hostnames.

---

## 🏗️ Role in System Architecture

```
                       +-------------------------+
                       | Hospital Server         |
                       | Eureka Discovery Server |
                       | (Port: 8761)            |
                       +------------+------------+
                                    ^
       +----------------------------+----------------------------+
       |                            |                            |
+------+------+              +------+------+              +------+------+
| API Gateway |              | Doctor      |              | Patient     |
| (Port 8080) |              | Service     |              | Service     |
+-------------+              | (Port 8081) |              | (Port 8082) |
                             +-------------+              +-------------+
                                    |
                             +------+------+
                             | Appointment |
                             | Service     |
                             | (Port 8083) |
                             +-------------+
```

---

## ⚙️ Configuration (`application.properties`)

```properties
spring.application.name=HospitalServer
server.port=8761

# Disable self-registration for the Eureka server instance
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
```

---

## 🛠️ Tech Stack

- **Java Version**: 17+
- **Spring Boot**: 3.x
- **Spring Cloud**: Netflix Eureka Server (`@EnableEurekaServer`)
- **Build Tool**: Maven

---

## 🚀 Getting Started

### 1. Prerequisites
- Java 17 or higher
- Maven 3.8+

### 2. Run Locally

```bash
# Clone the repository
git clone https://github.com/vaibhavdhardwivedi6-netizen/Hospital-Server.git
cd Hospital-Server

# Run using Maven wrapper
./mvnw spring-boot:run
```

---

## 🖥️ Eureka Web Dashboard

Once started, access the Eureka web console in your browser:

- **Dashboard URL**: [http://localhost:8761](http://localhost:8761)

The dashboard displays:
- Active registered microservice instances (`DOCTOR-SERVICE`, `PATIENT-SERVICE`, `APPOINTMENT-SERVICE`, `API_GETWAY`, `SPRING_SECURITY-JWT`).
- Instance IDs, status (UP/DOWN), hostnames, and ports.
- General server statistics, memory usage, and uptime.