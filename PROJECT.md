# Big Data Introduction – Final Project Instructions

## Overview

For your final evaluation, you will complete **one** of the two project options below. The goal is to demonstrate your understanding of Big Data concepts, tools, and architectures covered throughout the course.
You may choose either:

1. **Technical Project** – Hands-on setup and usage of a Big Data framework or tool.
2. **Conceptual Project** – A use-case-driven architectural design describing how Big Data tools work together to solve a real-world scenario.

Your submission must reflect your own understanding and thought process. While you may use external resources, the work must be genuinely produced by you and your teammate (**in a group of 2**) and **not a generic auto-generated document**. Structure, clarity, and conciseness are essential.

---

# Option A — Technical Project

### Goal

Install, configure, and run one Big Data related tool or framework, either:
-
* on your **local machine through Docker containers**, or
* on the **remote Hadoop cluster**.

### Deliverables

You will submit a **GitHub repository** with:

1. **A cohesive and self-contained README** containing:

   * Project title and short description
   * The chosen tool (e.g., Kafka, NiFi, Hive, HBase, Spark, etc.)
   * Why you selected this tool
   * Installation steps you performed
   * A minimal working example (e.g., a small Kafka producer–consumer, a NiFi flow, a Hive query on HDFS, a MapReduce job, etc.)
   * Screenshots or logs proving execution
   * Explanation of how this tool fits into a Big Data ecosystem
   * Any challenges encountered and how you solved them
   * A short section titled “My Setup Notes” describing something specific you learned or struggled with, including screenshots and log snippets, showcasing the problem solving process you handled.

2. **Folder structure** including:

   * configuration files, flows, docker-compose.yml, scripts, or code used
   * sample input/output data if applicable

Submissions lacking these elements will be considered incomplete.

---

# Option B — Conceptual Project (Non-Technical)

### Goal

Define a *realistic big data use case* and design a full architecture to support it.

Choose one use case (examples: E-commerce pipeline, IoT sensor ingestion, log analytics pipeline, etc.)

### Deliverables

Submit a **PDF document (max 6 pages)** containing:

### 1. Use Case Description

* The business problem
* The nature and expected volume of the data
* Why Big Data technologies are appropriate

### 2. Architecture Diagrams

Include clear diagrams showing:

* Data ingestion layer
* Storage layer (e.g., HDFS, cloud storage)
* Processing layer (MapReduce, Hive, Spark, NiFi, Kafka, etc.)
* Serving layer (reports, dashboards, downstream apps)
* Security/architecture considerations

### 3. Tools Explanation

For each tool you include (minimum 5 from the course: HDFS, YARN, MapReduce, Hive, HBase, Kafka, NiFi, cloud storage, etc.):

* What the tool is
* What problem it solves
* How it works (high-level)
* Why it fits your use case
* How it interacts with the other components

### 4. Workflow Description

Provide a **data flow diagram** + a **step-by-step description** of:

* How data enters the system
* How it is stored
* How it is processed
* How results are delivered

### 5. Critical Thinking Requirement (Anti-AI safeguard)

Include a short section titled **"Design Justification Choices"** where you:

* Explain two design decisions you made
* Explain one alternative you considered and why you didn’t choose it

This content must reflect your own reasoning—not automatically generated output.
