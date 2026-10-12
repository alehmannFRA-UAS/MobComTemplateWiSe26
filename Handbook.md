# Mobile Computing Winter Semester 2026/27

## Purpose of the Module
This module combines Mobile Computing, 5G/6G networks, AI, agent systems, and network automation. The course is built around seminar presentations and a hands-on team project.

## Learning Objectives
- Understand modern mobile network architectures
- Apply AI agents for network automation
- Develop scientific research and presentation skills
- Design, implement, and evaluate a prototype

## Seminar Presentations
- 15–20 minute presentation plus discussion
- Presentation slides (PDF)
- Handout (2–4 pages)
- Reference list
- Live demonstration or reproducible example recommended

### Specific Proposal for Seminar Organization
The topics are not assigned to students at random,
but are integrated with the project groups.
The presentations also serve as the technical foundation for the project!
By the end, each group must not only have a thorough understanding of its own project, but must also be familiar with the presentations given by the other groups, as these cover relevant topics.

### Important Teaching Guidelines
Every presentation should follow the same structure:
1. Problem: What problem does the technology solve?
2. Concept: How does it work?
3. Technical Implementation: What protocols, APIs, algorithms, or components are involved?
4. Example: A concrete example from a mobile network scenario
5. Project Relevance: How could the technology be used in the project?
6. If possible, a 5-minute live demo, a reproducible example, or a discussion

## Schedule for Lectures and Project
|Week       |Date             |Lecture                                                           |Project (M = Milestone)                                  |
|-----------|-----------------|------------------------------------------------------------------|---------------------------------------------------------|
|1          |October 12, 2026 |Introduction/Organization and Assignment of Presentation Topics   |                                                         |
|2          |October 19, 2026 |Brief Introduction to the Repository and Project Topics           |                                                         |
|3          |October 26, 2026 |First presentations (approx. 4, 15–20 min each + 5 min Q&A)       |                                                         |
|4          |November 2, 2026 |Second presentations (4 presentations)                            |                                                         |
|5          |November 9, 2026 |Third presentations (4 presentations)                             |                                                         |
|6          |November 16, 2026|Fourth presentations (4 presentations)                            |                                                         |
|7          |November 23, 2026|Fifth presentations (4 presentations)                             |                                                         |
|8          |November 30, 2026|Sixth presentations (4 presentations)                             |                                                         |
|7          |November 23, 2026|Fifth presentations (4 presentations)                             |                                                         |
|8          |November 30, 2026|Sixth presentations (4 presentations)                             |                                                         |
|9          |December 7, 2026	|Seventh presentations (4 presentations)                           |                                                         |
|10         |December 14, 2026|Eighth presentations (4 presentations)                            |                                                         |
|11         |January 4, 2027  |Ninth presentations (4 presentations)                             |Create a GitHub repository                               |
|12         |January 11, 2027 |Tenth presentations (4 presentations)                             |Understanding the environment and building the foundation|
|13         |January 18, 2027 |Eleventh presentations (4 presentations)                          |M1: Architecture and use cases                           |
|14         |January 25, 2027 |Twelfth presentations (4 presentations) [Total: 48]               |M2: AI/Agent Concept and Initial Prototypes              |
|15         |February 1, 2027 |							                                                     |Tool/API/MCP Integration                                 |
|16         |February 8, 2027 |                                                                  |Implementation                                           |
|17         |February 15, 2027|                                                                  |Implementation + Experiments                             |
|18         |February 22, 2027|                                                                  |M3: Tests and Measurements                               |
|19         |March 1, 2027    |                                                                  |M4: Evaluation, Documentation, Presentation Preparation  |
|20         |March 8, 2027    |                                                                  |Project presentations + demonstration                    |

## Workflow for Students
1. Use the [Template] (https://github.com/alehmannFRA-UAS/MobComTemplateWiSe26)  
   Each project group creates its own repository from MobComTemplateWiSe26.
2. One Repository per Group  
   The group works exclusively in this repository. This ensures that code, documentation, configuration, and results are all stored in one central location.
3. Repository as Project Documentation  
   The GitHub repository should not only serve as a place to submit the code, but also document the entire development process:
   - Problem statement / project idea
   - Architecture
   - Implementation
   - Configuration
   - Tests and measurement results
   - Screenshots or Wireshark captures
   - Sources
   - Problems and their solutions, if applicable
4. Use Git effectively  
   Students are expected to commit regularly.
   This also makes it possible to track how the project has evolved.
   GitHub itself describes commits as snapshots of the project’s status and branches as a way to work on changes in parallel.
5. Develop the presentation based on the repository  
   The presentation should ultimately showcase the project’s key results and, in particular, demonstrate the technical implementation.
   The repository serves as the foundation for the presentation.

## Mandatory Project Structure
All project work must be carried out entirely in the designated GitHub repository.  
The repository serves as both the technical foundation and the project documentation.  
Changes to the project must be documented regularly via Git commits during the project period (10 weeks).  

README.md  
task.md  
docs/  
├── architecture.md  
├── implementation.md  
├── testing.md  
└── presentation.md  
configs/  
compose-files/  
build-files/  
src/  
tests/  
results/  
├── screenshots/  
├── wireshark/  
└── measurements/  

## Overarching Project Theme
“AI-Supported Automation, Monitoring, and Optimization of Mobile Telecommunications Networks”

Core Idea: Students develop AI-based systems that not only analyze a mobile telecommunications network,  
but are also increasingly capable of independently building, configuring, monitoring, diagnosing, optimizing, and maintaining it.

    ┌──────────────────────┐
    │        User          │
    │   Natural Language   │
    └──────────┬───────────┘
               │
               ▼
    ┌──────────────────────┐
    │      AI / Agent      │
    │   Reasoning / LLM    │
    └──────────┬───────────┘
               │
         MCP / Tools / APIs
               │
               ▼
    ┌─────────────────────────────────────────┐
    │        Network Management Layer         │
    │                                         │
    │ Create | Configure | Monitor | Diagnose │
    │ Optimize | Repair | Experiment          │
    └───────────────────┬─────────────────────┘
                        │
                        ▼
    ┌─────────────────────────────────────────┐
    │             Mobile Network              │
    │                                         │
    │ Docker | Open5GS | UERANSIM |           │
    │ PacketRusher                            │
    └─────────────────────────────────────────┘

## Groups with different tasks
Everyone uses the same GitHub template and the same network environment,
but each group works on a different part of the “AI Network Lifecycle.”
e.g., dividing into 6 groups
|Group  |Topic                      |Key Question                                                            |
|-------|---------------------------|------------------------------------------------------------------------|
|1      |AI Network Provisioning    |Can an AI independently set up and configure a 5G network?              |
|2      |AI Network Monitoring      |Can an AI monitor the network’s status and detect anomalies?            |
|3      |AI Troubleshooting         |Can AI independently analyze and resolve network errors?                |
|4      |AI Network Optimization    |Can AI optimize the network based on measurement data?                  |
|5      |MCP Network Controller     |Can an MCP server make the entire 5G test network controllable?         |
|6      |Autonomous Network Agent   |Can an agent combine the other capabilities and act autonomously?       |

### Group 1 – AI Network Provisioning
Students will develop an agent that receives, for example, the following request:  
“Create a 5G network with an AMF, SMF, UPF, and two UEs. Configure a subscriber with IMSI ..., APN ..., and then start both UEs.”

The AI must derive actions from this.  
For example:  
User --> “Create a 5G network...” --> LLM Agent  
                                          │  
                                          ├── create_config()  
                                          ├── add_subscriber()  
                                          ├── start_open5gs()  
                                          ├── start_ueransim()  
                                          └── test_connectivity()  

The AI doesn’t simply generate random files; instead, it must:  
1. Understand requirements
2. Generate configuration
3. Validate configuration
4. Start container
5. Configure UERANSIM
6. Register UE
7. Test connectivity
8. Detect errors

Result: AI-based Network Provisioning Assistant  

### Group 2 – AI Network Monitoring (Measurement Data and Observability)
Students will build a system that monitors, for example, Open5GS logs, Docker container status, CPU/RAM, network traffic,  
UE registration, PDU sessions, ping/throughput, packet loss, and latency.  
The AI should be able to answer questions such as:  
“Why can’t UE2 establish a PDU session?” or “Has the network status changed in the last five minutes?”  
This could also give rise to two variants, e.g.:  
 - rule-based monitoring
 - AI-based anomaly detection
The two methods could be compared.  

### Group 3 – AI Troubleshooting
The group must address intentionally faulty network configurations.  

For example: UE --> gNB --> AMF -x-> SMF --> UPF  

Possible errors:  
 - incorrect IP address
 - incorrect TAC
 - incorrect PLMN
 - incorrect IMSI
 - Incorrect DNN
 - Incorrect port
 - Container not started
 - Routing problem
 - Missing route
 - Incorrect subscriber configuration

For example, the agent receives: “UE 1 cannot connect to the Internet. Find the error.”  

It then gathers information and processes the following steps, for example:  
1. Gather information (Docker status | Open5GS logs | UERANSIM logs | Network configuration | ping | tcpdump)
2. Packet analysis
3. LLM reasoning
4. Hypothesis
5. Fix
6. Verification

### Group 4 – AI Network Optimization
For example:  
“Optimize the network for minimum round-trip time while maintaining a throughput of at least 50 Mbit/s.”  
or  
“Find a configuration that reduces resource consumption without deteriorating QoS.”

The AI receives measurement data such as: latency, packet loss, throughput, CPU, memory, number of UEs, session setup time, etc.,  
and is allowed to modify certain parameters.

The AI then performs the following sequence, for example:  
Configuration --> Experiment --> Measurement --> AI evaluation --> New configuration --> Experiment --> ...

This creates a small closed-loop optimization process.  
Here, different approaches could be compared, such as: LLM reasoning, heuristic optimization, classical optimization methods, and reinforcement learning  

### Group 5 – MCP Network Controller
The group is developing an MCP server that abstracts the mobile telecommunications network.  
For example, using the following MCP tools:
 - get_network_status()
 - get_ue_status()
 - get_pdu_sessions()
 - start_network()
 - stop_network()
 - restart_component ()
 - create_subscriber()
 - delete_subscriber()
 - get_logs()
 - get_metrics()
 - capture_traffic()
 - run_ping()
 - run_iperf()
 - change_configuration()

Using these functions, any MCP-capable agent could interact with the network.

### Group 6 – Autonomous Network Agent (more challenging)
This group integrates as many of the other groups’ capabilities as possible and uses them to develop an autonomous network agent.

For example:  
“Operate the 5G network. Ensure that all UEs are registered and that the PDU sessions are functioning. If problems arise, diagnose and resolve them.”

## Individual Projects Interconnect (Illustrative Overview)

                    Autonomous
                   Network Agent
                         ▲
                         │
            ┌────────────┴────────────┐
            │                         │
     Troubleshooting          Optimization
            ▲                         ▲
            │                         │
            └────────────┬────────────┘
                         │
                    MCP Interface
                         ▲
                         │
                Network Controller
                         ▲
                         │
       ┌─────────────────┴─────────────────┐
       │                                   │
    Monitoring                     Provisioning
       │                                   │
       └─────────────────┬─────────────────┘
                         │
                         ▼
      Open5GS / UERANSIM / PacketRusher
                         │
                         ▼
                       Docker

## Key Requirement for the Project

Each group must define at least one measurable network use case.

For example:
“The developed agent must detect the error in at least 4 out of 5 intentionally generated error cases
and propose an appropriate corrective action.”
or
“The agent must automatically deploy a defined 5G test network based on a natural language description.”
or
“The optimization agent must achieve an
improvement in the defined objective function of at least X% compared to the initial configuration.”


## Structure of the Lecture Sessions
Students are to give individual presentations on a topic that is thematically related to the projects.

For example, the topics could be divided into five blocks:
|Block |Topic Area          |Objective                                                    |
|------|--------------------|-------------------------------------------------------------|
|A     |Mobile Networks     |Open5GS, 5G Core, UERANSIM, Network Functions                |
|B     |AI & LLM            |LLMs, RAG, Agents, Tool Use                                  |
|C     |MCP & Integration   |MCP, APIs, Function Calling, Security                        |
|D     |AI for Networks     |Monitoring, Anomaly Detection, Troubleshooting, Optimization |
|E     |Autonomous Networks |Closed Loop, Self-Healing, Digital Twins, Evaluation         |
|G     |Research & Future   |O-RAN, 6G Vision and AI-Native Networks, Autonomous Networks |

## Specific Topic Plan
### Block A – Mobile Networks
1. 5G System Architecture
   Key Question:
   “How does a modern 5G network work, and which components must be understood for the project?”

   Content:
    - 5G System Architecture
    - UE
    - gNB
    - 5G Core
    - AMF
    - SMF
    - UPF
    - AUSF
    - UDM
    - NRF
    - NSSF
    - SBI
    - Control Plane / User Plane
    - Registration
    - PDU Session Establishment

2. 5G Core Network – Open5GS
   Key Question:
   “How is Open5GS structured, and how can a 5G Core be configured and operated?”

   Contents:
    - Architecture
    - Network Functions
    - Configuration Files
    - Database/MongoDB
    - SBI
    - Logs
    - REST/API Capabilities
    - Docker Deployment

3. UERANSIM and PacketRusher
   Key Question:
   “How can a 5G network be simulated or tested without actual (radio) hardware?”

   Content:
    - UERANSIM
    - gNB
    - UE
    - PacketRusher
    - Registration
    - PDU Session
    - Traffic Generation
    - Typical error scenarios

4. 5G Network Slicing
   Key Question:
   “How could AI determine which slice requires which resources?”

   Content:
    - Network Slices
    - S-NSSAI
    - QoS/5QI
    - Isolation
    - Different Requirements

### Block B – AI and LLM
5. Large Language Models (LLMs)
   Key Question:
   “What can an LLM actually do—and what can’t it do?”

   Content: (Not as an introduction to AI, but with a focus on its technical use as an agent!!!)
    - Transformer
    - Token
    - Context Window
    - Prompt
    - Inference
    - Temperature
    - Hallucination
    - Reasoning
    - Structured Output

6. Prompt Engineering and Structured Output
   Key Question:
   “What should be considered in prompt engineering, and how can one achieve well-structured output?”

   Content:
    - System Prompt
    - User Prompt
    - Few-Shot
    - Chain of Thought – Conceptually
    - JSON Output
    - Schema Validation
    - Function Calling


7. Retrieval-Augmented Generation (RAG)
   Key Question:
   “How can an AI work with project-specific knowledge?”

   Content:
    - Embeddings
    - Vector Database
    - Retrieval
    - RAG Pipeline
    - Documents
    - Logs
    - RFCs and 3GPP TS
    - Open5GS Documentation

   Example: “Why does the registration of UE3 fail?”
   The AI can draw on Open5GS documentation and its own network documentation.

8. AI Agents
   Key Question:
   “What is an agent?”

   Content:
    - LLM vs. Agent
    - Goal
    - Planning
    - Tools
    - Memory
    - Observation
    - Action
    - Reflection
    - Agent Loop

9. Multi-Agent Systems
   Key question:
   “When and how to use multiple agents?”

   Content:
    - Communication between agents
    - Role allocation
    - Coordination
    - Conflicts
    - Advantages/Disadvantages

### Block C – MCP and System Integration
10. Model Context Protocol (MCP)
    Key Question:
    “Why is MCP relevant to network automation?”

	Contents:
     - What is MCP
     - MCP Client
     - MCP Server
     - Tools
     - Resources
     - Prompts
     - Tool Discovery
     - Tool Invocation
     - JSON-RPC
     - Transport

11. Developing Your Own MCP Server
    Key Question:
	“How can an MCP server be implemented?”

    Contents:
     - Practical examples (e.g., get_ue_status()|restart_open5gs()|get_open5gs_logs()|get_network_metrics()
     - Design patterns
     - Architecture

12. Function Calling and Tool Use
    Key question:
	“What distinguishes the MCP from agents, and how can they interact?”

    Content:
     - Function Calling
     - Tool Selection
     - Tool Schema
     - Parameters
     - Validation
     - Tool Results
     - Error Handling

    Example: User: “Why is UE 2 offline?”; LLM: get_ue_status(2); Result: REGISTERED = false; LLM: get_logs(“AMF”); Result: authentication failure

13. APIs for Network Automation
    Key Question:
    “How can software programmatically control a telecommunications network?”

    Content:
     - REST
     - HTTP
     - JSON
     - WebSocket
     - gRPC
     - NETCONF/RESTCONF
     - OpenAPI
     - CLI Automation

14. Containerization and Network Automation (Security)
    Key Question:
    “How can an agent use/control Docker without gaining arbitrary shell access?”

    Contents:
     - Docker
     - Docker Compose
     - Container Networking (Cloud-Native Networking (CNF))
     - Volumes
     - Environment Variables
     - Health Checks
     - Service Dependencies
     - Logs
     - Container Lifecycle
     - Standardization (e.g., ETSI)

### Block D – AI for Network Management
15. Network Monitoring and Observability
    Key Question:
    “What does monitoring entail, and how can it be performed?”

    Contents:
	 - Monitoring
     - Metrics
     - Logs
     - Traces
     - Events
     - Telemetry
     - KPIs
     - Prometheus/Grafana
     - OpenTelemetry

16. Anomaly Detection in Networks
    Key Question: (Example: Is the following an anomaly? The registration rate suddenly drops by 30%)
	“What is an anomaly?”

    Contents:
     - Normal State
     - Anomaly
     - Outlier
     - Statistical Detection
     - Clustering
     - Autoencoder
     - Time Series
     - Thresholds

17. AI-Based Network Troubleshooting
    Key Question:
    “How can AI identify the root cause of the error?”

    Contents:
     - Fault Detection
     - Fault Localization
     - Root Cause Analysis
     - Log Analysis
     - Correlation
     - Hypothesis Generation
     - Automated Diagnosis

18. AI-Based Network Optimization
    Key Question:
    “Can an agent find the optimal configuration, for example, through experimentation?”

    Contents:
     - Optimization Problem
     - Objective Function
     - Constraints
     - Parameters
     - Feedback
     - Experiment
     - Evaluation

### Block E – Autonomous Networks
19. Closed-Loop Automation / Intent-Based Networking
    Key Question:
    “How can KPIs, for example, be communicated to the system in a way that is understandable using natural language?”

	Contents:
     - For example, the operator says: “Make sure latency stays below 20 ms,” rather than “Set parameter X to 42.”
     - Intent
     - Policy
     - Measurement

20. Self-Healing Networks
    Key question:
    “Can a network detect and correct errors on its own?”

	Content:
     - Failure
     - Detection
     - Diagnosis
     - Decision
     - Repair
     - Verification

21. AI Security / Security of AI Agents
    Key Question:
    “What happens if the AI makes a wrong decision?”

    Content:
     - Prompt Injection
     - Tool Abuse
     - Privilege Escalation
     - Malicious Input
     - Secret Management
     - Sandboxing
     - Least Privilege
     - Human-in-the-Loop

22. AI Evaluation
    Key Question:
    “How can we verify that the agent works?”

    Contents:
     - Accuracy
     - Precision/Recall
     - Success Rate
     - False Positives
     - False Negatives
     - Latency
     - Cost
     - Reproducibility
     - Benchmarking

23. Digital Twins for Mobile Networks
    Key Question:
    “Can changes be tested in a digital twin first before implementing them in the live network?”

    Content:
     - DTN (ITU) vs. NDT (IETF)
	   - DTN/NDT vs. Digital Twins
     - Framework and functional requirements
     - Capability levels and evaluation methods

### Block G – Research & Future
24. O-RAN
    Key Question:
    “What is O-RAN, why is O-RAN important, and how does it relate to AI?”

	Contents:
     - Architecture
     - RIC
     - xApps
     - rApps
     - O-RAN Alliance

25. 6G Vision and AI-Native Networks
    Key question:
    “What is the current 6G vision toward so-called AI-Native Networks?”

    Contents: Different perspectives from, for example:
	 - Manufacturers such as Ericsson, Nokia, and Huawei
     - Organizations such as 6G-IA, ETSI, NGMN Alliance, and Next G Alliance
     - Research, e.g., the four national 6G transfer hubs: 6GEM, 6G-life, 6G-RIC, and Open6GHub

