# Documentation on Frontend-API


---

## Author Information
| Created by      | Created on  | Version | Last updated  | Pre Reviewer | 
|-----------------|------------|---------|-----------------|--------------| 
| Sunny kumar | 06-08-2025 | V 1.0   | 06-08-2025      | Aman Raj       | 


---

<details>
  <summary><strong> Table of Contents</strong></summary>


1. [Purpose](#2-purpose)  
2. [Pre-Requisites](#3-pre-requisites)  
3. [System Requirements](#4-system-requirements)   
4. [Ports](#5-ports)
5. [Architecture](#5-Architecture)
6. [Dataflow Diagram & Steps](#5-Dataflow-Diagram-&-Steps)
7. [Installation of Frontend API](#6-Installation-of-Frontend-API)   
8. [Troubleshooting](#7-troubleshooting)   
9. [Contact Information](#9-contact-information)  
10. [References](#10-references) 
</details>

---
## Purpose

The OT-MICROSERVICES Frontend is a ReactJS web application that provides the main user interface for the OT-Microservices stack. It enables management and visualization of employee, attendance, and salary information by communicating with the backend REST APIs.

---

## Pre-requisites

| **Dependency** | **Version** |
| -------------- | ----------- |
| Node.js        | v12.22.9    |
| npm            | v8.5.1      |
| GNU Make       | v4.3        |




---
## System Requirements

| Hardware/Software | Minimum Recommendation  |
|-------------------|------------------------|
| Processor         | 1 CPU (t2.micro EC2)   |
| RAM               | 1 GiB                  |
| Disk              | 8 GB                   |
| OS                | Ubuntu 22.04 LTS       |

---




## Ports


| Port | Service              | Description                         |
|------|---------------------|-------------------------------------|
| 22   | SSH                 | Remote terminal access              |
| 3000 | HTTP (ReactJS)      | Default frontend port               |


---


## Architecture

**Description:**  
This architecture diagram shows a front-end web app interacting with three microservices—Employee API, Salary API, and Attendance API—via REST endpoints. 

<img width="2912" height="1156" alt="image" src="https://github.com/user-attachments/assets/1ad6e178-6e0c-471d-a831-f2659d742dd3" />


---

## Dataflow Diagram & Steps

| Step | Component        | Action                                                                 |
|------|------------------|------------------------------------------------------------------------|
| 1    | **User**         | Interacts with UI to view/add/update employee data                     |
| 2    | **Frontend UI**  | Sends HTTP request to Employee API                                     |
| 3    | **Employee API** | Validates request, applies business logic, checks Redis cache          |
| 4a   | **Redis** (Cache Hit) | Returns cached data to API                                             |
| 4b   | **Redis** (Cache Miss) → **ScyllaDB** | If data is not cached, fetches from DB and may update Redis          |
| 5    | **Employee API** | Returns structured JSON response to UI                                 |
| 6    | **Frontend UI**  | Renders data as table view / confirmation / error message              |

---


<img width="500" height="600" alt="data flow-employee" src="https://github.com/user-attachments/assets/f8435420-a354-419c-a5e0-70d99129cd42" />

---



## Installation of Frontend API

_Follow this link for full installation guide_  
(**[Click here to view installation guide](https://github.com/Snaatak-Apt-Get-Swag/documentation/blob/SCRUM-76-ishaan/OT-Microservices/Applications/Frontend-API/POC/README.md)**)


---

## Troubleshooting

| Issue                        | Solution                                                         |
|------------------------------|------------------------------------------------------------------|
| JS heap out of memory        | Use `NODE_OPTIONS="--max_old_space_size=4096" npm run build`     |
| Port 3000 in use             | Run `serve -s build -l 3001` or kill previous process            |
| Cannot access externally     | Check firewall/security group for port 3000                      |
| Deprecated/vulnerable dependencies   | Run `npm audit fix` (optional, not blocking for deployment)      |                           |

---



## Contact Information

| **Field** | **Details**                                                                     |
| --------- | ------------------------------------------------------------------------------- |
| Name      | Sunny Kumar                                                                     |
| Email     | [sunny.kumar.snaatak@mygurukulam.co](mailto:sunny.kumar.snaatak@mygurukulam.co) |

---

## References


| Description                       | Link                                                                 |
|------------------------------------|----------------------------------------------------------------------|
| Frontend API                       | https://github.com/OT-MICROSERVICES/frontend                         |
| Javascript heap out of memory      | https://geekflare.com/fix-javascript-heap-out-of-memory-error/       |
