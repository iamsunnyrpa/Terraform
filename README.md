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

# Terraform Installation on Linux

Here are the steps to install Terraform on Linux. The exact method might vary slightly depending on your specific distribution (e.g., Ubuntu, CentOS, Fedora).

## Method 1: Using the HashiCorp Repository (Recommended for Package Management)

This method allows you to easily update Terraform in the future using your system's package manager.

### For Debian/Ubuntu based systems:

1.  **Install prerequisites:**
    ```bash
    sudo apt update
    sudo apt install -y gnupg software-properties-common curl
    ```

2.  **Add the HashiCorp GPG key:**
    ```bash
    curl -fsSL [https://apt.releases.hashicorp.com/gpg](https://apt.releases.hashicorp.com/gpg) | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
    ```

3.  **Add the official HashiCorp repository:**
    ```bash
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] [https://apt.releases.hashicorp.com](https://apt.releases.hashicorp.com) $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
    ```

4.  **Update the package list:**
    ```bash
    sudo apt update
    ```

5.  **Install Terraform:**
    ```bash
    sudo apt install terraform
    ```

### For Red Hat based systems (CentOS, Fedora, etc.):

1.  **Install `yum-utils`:**
    ```bash
    sudo yum install -y yum-utils
    ```
    or for Fedora:
    ```bash
    sudo dnf install -y dnf-plugins-core
    ```

2.  **Add the official HashiCorp repository:**
    For CentOS/RHEL:
    ```bash
    sudo yum config-manager --add-repo [https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo](https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo)
    ```
    For Fedora:
    ```bash
    sudo dnf config-manager --add-repo [https://rpm.releases.hashicorp.com/fedora/hashicorp.repo](https://rpm.releases.hashicorp.com/fedora/hashicorp.repo)
    ```

3.  **Install Terraform:**
    For CentOS/RHEL:
    ```bash
    sudo yum -y install terraform
    ```
    For Fedora:
    ```bash
    sudo dnf -y install terraform
    ```

## Method 2: Manual Installation (Downloading the Binary)

This method is more generic and works across most Linux distributions.

1.  **Download Terraform:**
    Visit the [Terraform downloads page](https://www.terraform.io/downloads.html) and find the link for your Linux architecture (usually AMD64). You can use `wget` in the terminal to download it. For example, to download the latest version (check the website for the actual latest version):
    ```bash
    wget [https://releases.hashicorp.com/terraform/](https://releases.hashicorp.com/terraform/)<LATEST_VERSION>/terraform_<LATEST_VERSION>_linux_amd64.zip
    ```
    Replace `<LATEST_VERSION>` with the actual latest version.

2.  **Install `unzip` if you don't have it:**
    ```bash
    sudo apt update
    sudo apt install -y unzip
    ```
    or
    ```bash
    sudo yum install -y unzip
    ```
    or
    ```bash
    sudo dnf install -y unzip
    ```

3.  **Unzip the downloaded file:**
    ```bash
    unzip terraform_<LATEST_VERSION>_linux_amd64.zip
    ```

4.  **Move the `terraform` binary to a directory in your system's PATH** (e.g., `/usr/local/bin`):
    ```bash
    sudo mv terraform /usr/local/bin/
    ```

## Verify Installation

After either method, verify the installation by opening a new terminal and running:

```bash
terraform --version
