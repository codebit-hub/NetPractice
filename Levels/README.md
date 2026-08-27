*This project has been created as part of the 42 curriculum by dporhomo.*

## Description

This project focuses on practical network configuration, requiring the calculation and assignment of IP addresses, subnet masks, and routing tables to make non-functioning network topologies operational.

## Objective
The primary goal of this project is to develop a practical understanding of how network addressing and routing operate at the Network Layer (Layer 3 of the OSI model) through:
*   Calculating subnets, broadcast addresses, and valid host ranges using CIDR notation.
*   Optimizing IP allocation using Variable Length Subnet Masking (VLSM).
*   Configuring static routing tables, default gateways (`0.0.0.0/0`), and specific network routes.
*   Troubleshooting multi-hop routing issues, particularly identifying and fixing "Return Path" failures.
*   Understanding the mechanics of switches (Layer 2) versus routers (Layer 3).
*   Differentiating between Public and Private IP addresses and understand their routability rules across the Internet.

## Instructions

* **Execution:** Download and extract `net_practice.1.9.tgz`. Run `./run.sh` to launch the local web server and open the interface. Alternatively, run `python3 -m http.server 49242` and navigate to `http://localhost:49242`. Enter your login to load personal configurations.
* **Usage:** Use the **training** tab to practice and the **evaluation** tab to generate random configurations for grading. Use the interface logs to diagnose missing gateways or invalid IPs.
* **Export:** Click **[Get my config]** upon completing a level to download the `.json` file containing your valid configuration.
* **Submission & Evaluation:** Place all 10 exported `.json` files at the root of your Git repository. During the defense, you must successfully configure three random levels under a time limit without external tools, though a basic calculator (`bc`) is permitted.

## Levels Overview

| Level | Topology | Core Skills Tested |
| --- | --- | --- |
| **1** | 2 public hosts, `/24` & `/16` subnets | Basic IP addressing and CIDR boundaries. |
| **2** | 2 private hosts, `/27` & `/30` subnets | Subnet allocation and minimizing host waste. |
| **3** | 3 public hosts via a switch | Switch mechanics and shared local broadcast domains. |
| **4** | 3 public hosts via a router (3 interfaces) | Router interfaces acting as specific subnet gateways. |
| **5** | 2 public hosts via a router (2 interfaces) | Cross-subnet IP routing and next-hop logic. |
| **6** | 1 public host via switch, router, Internet | Default routes (`0.0.0.0/0`) and internet gateways. |
| **7** | 2 public hosts via 2 separate routers | Multi-hop forward routing and return-path configuration. |
| **8** | 2 public hosts via consecutively connected routers | Variable Length Subnet Masking (VLSM) and route summarization. |
| **9** | 3 public subnets via 2 routers | Preventing subnet overlap and handling RFC 1918 public/private IP rules. |
| **10** | 4 public hosts via 2 routers and a switch | Advanced VLSM, supernetting, and comprehensive network design. |

## Usage Example: Level 8

In Level 8, the goal is to connect two hosts to the Internet through two chained routers. The challenge involves strict constraints: one host requires a `/28` mask, and the Internet node has a fixed return route of `/26`. The solution requires combining two `/28` host networks into a logically adjacent block, allowing the first router to use a single `/27` summary route. Additionally, a `/30` mask is used to optimize the point-to-point transit link between the two routers, demonstrating efficient IP allocation while solving the "Return Path Trap".

## Resources

* **Networking Concepts:** TCP/IP 4-Layer model, OSI layers, subnet masks, default gateways, routing tables, and switches.
* **References:** [Subnet IPv4 Calculator](https://subnetipv4.com/#learn), Wikipedia (IPv4, IP Address), and YouTube tutorials ([Network Direction](https://www.youtube.com/watch?v=s_Ntt6eTn94), [Subnetting Mastery](https://www.youtube.com/watch?v=CGmTvukObOw)).
* **AI Usage:** I operate as a technical sounding board. For this project, I assisted in diagnosing multi-hop return path failures, explaining VLSM mechanics, determining non-overlapping IP boundaries and distinguishing between public and private IP constraints across the TCP/IP stack.