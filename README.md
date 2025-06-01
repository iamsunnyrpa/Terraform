# This document outlines the key differences between Terraform and Ansible.

## Terraform

**Terraform** is an open-source Infrastructure as Code (IaC) tool by HashiCorp. It focuses on defining and provisioning infrastructure using a declarative configuration language (HCL).

**Key characteristics:**

* **Infrastructure Provisioning:** Primarily designed for creating, updating, and deleting infrastructure resources.
* **Declarative:** You define the desired state of your infrastructure, and Terraform figures out how to achieve it.
* **State Management:** Maintains a state file to track the current configuration of your infrastructure.
* **Multi-Cloud:** Supports numerous cloud providers and services.
* **Immutable Infrastructure:** Often promotes an immutable approach to infrastructure changes.
* **Agentless:** Does not require agents on the managed infrastructure.


**Key characteristics:**

* **Configuration Management:** Excels at configuring existing systems and deploying software.
* **Imperative/Procedural (with declarative aspects):** You typically define the steps to reach a desired state.
* **No Built-in State Management:** Relies on the execution of tasks to achieve the desired configuration.
* **Wide Scope:** Can manage cloud, on-premises, and network infrastructure.
* **Mutable Infrastructure:** Commonly used for making changes to existing systems.
* **Agentless:** Communicates via SSH or WinRM.

## Key Differences Summarized

| Feature                 | Terraform                                     | Ansible                                          |
| :---------------------- | :-------------------------------------------- | :----------------------------------------------- |
| **Primary Focus** | Infrastructure Provisioning (Orchestration)   | Configuration Management, Application Deployment |
| **Approach** | Declarative                                   | Imperative/Procedural (with declarative aspects) |
| **State Management** | Built-in, crucial for operation              | No built-in state management                   |
| **Infrastructure Type** | Primarily cloud infrastructure                | Cloud, on-premises, network devices, etc.        |
| **Mutability** | Often leads to immutable infrastructure       | Typically used for mutable infrastructure        |
| **Agent Requirement** | Agentless                                     | Agentless                                        |

## In Simple Terms

* **Terraform:** Builds the infrastructure (the house).
* **Ansible:** Configures and maintains what's inside the infrastructure (furnishing and maintaining the house).

## Using Them Together

It's common to use Terraform to provision infrastructure and then Ansible to configure the software on that infrastructure.
