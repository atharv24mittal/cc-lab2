# CC Lab 2 – Monolithic Architecture Optimization

## Project Overview

This project demonstrates a **monolithic FastAPI application** for a college fest system with features like:

* User Registration & Login
* Event Listing
* Event Registration
* My Events Dashboard
* Checkout

The lab focuses on understanding **monolithic architecture drawbacks** such as:

* Single point of failure
* Performance bottlenecks
* Tight coupling

We used **Locust** for load testing and optimized routes to improve performance.

---

## Optimized Routes

### Route 1: `/events`

**1. What was the bottleneck?**
The `/events` route contained an intentional CPU-intensive loop that performed millions of unnecessary computations, causing artificial delay in every request.

**2. What change did you make?**
Removed the wasteful computation loop from the route logic and kept only the required database query and template rendering.

**3. Why did the performance improve?**
Because unnecessary CPU processing was eliminated, the server spent less time per request, reducing response time and improving overall performance.

---

### Route 2: `/my-events`

**1. What was the bottleneck?**
The `/my-events` route also contained an artificial delay loop that performed unnecessary iterations, increasing execution time for each request.

**2. What change did you make?**
Removed the dummy computation loop and retained only the database join query and template rendering logic.

**3. Why did the performance improve?**
Eliminating redundant computations reduced CPU load, resulting in faster request processing and better response times.

---

### Route 3: `/checkout` (from Part 8)

**1. What was the bottleneck?**
The checkout logic used inefficient iterative computation to calculate total fee, increasing processing time.

**2. What change did you make?**
Replaced inefficient looping logic with optimized aggregation logic.

**3. Why did the performance improve?**
Optimized computation reduced algorithmic complexity and execution time, improving response speed.

---

## Tools Used

* **FastAPI** – Backend framework
* **SQLite** – Database
* **Locust** – Load testing tool
* **Jinja2** – Template engine

---

## Learning Outcome

This lab demonstrates that in a **monolithic architecture**, inefficient code in a single route affects the entire system performance because all components share the same runtime. Optimizing even small sections of code can significantly improve overall system performance.

---

## Author

SRN: PES2UG23CS103
