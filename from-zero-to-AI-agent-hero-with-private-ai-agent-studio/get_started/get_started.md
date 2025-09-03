# Get Started

## Introduction

In this lab, you will set up the prerequisites required to install Oracle Private AI Agent Studio on your OCI Virtual Machine (VM).

**Estimated Time**: 10 minutes.

## Prerequisites

- Access to a VM with sudo privileges and at least 60 GB of available disk space.

## Objectives

By the end of this lab, you will be able to:

- Ensure your compute environment meets all requirements for deploying Oracle Private AI Agent Studio.
- Install and configure Podman.
- Locate and follow official documentation.

## Task 1: Install and setup Podman

Podman is a container engine that is essential for preparing the key components required to install and run Oracle Private AI Agent Studio.

The installation steps may vary depending on your system and environment. We provide the instructions to install it in an OCI VM. If that is not your case, please refer to our [setup guide](http://applied-ai-stage.oraclecorp.com:8000/25.3.0.0/index.html) and follow the instructions that best suit your environment.

> **Important**.
>
> Run the installation as a non-root user. Podman must be set up and used in rootless mode for Oracle Private AI Agent Studio installations. Do not perform the installation or run deployment steps as the root user. Please use an OL8 VM for the installation.

Before you start the installation, ensure you select a mount point with at least 60 GB of available space. Anywhere in this document where `<mount_point>` appears, replace it with your chosen mount point that meets this requirement. Make sure it is not an NFS mount. Avoid using directories under /home as the mount point, directories under /scratch are recommended.

### Install Podman

To install podman run the following command:

```bash
<copy>
sudo yum install podman
</copy>
```

### Disable SELinux

SELinux on OCI VMs can prevent Podman from loading some of the necessary libraries. Set SELinux to permissive mode by running the following command:

```bash
<copy>
sudo setenforce permissive
</copy>
```

### Setup Podman to use storage with enough space

1. Create a new directory to host Podman files

    ```bash
    <copy>
    mkdir -p <mount_point>/podman_storage/storage/graphroot
    mkdir -p <mount_point>/podman_storage/storage/runroot
    </copy>
    ```

2. Create ~/.config/containers

    ```bash
    <copy>
    mkdir -p ~/.config/containers
    </copy>
    ```

3. Run `vi ~/.config/containers/storage.conf` and paste below contents

    ```bash
    <copy>
    [storage]
    driver = "overlay"
    graphroot = "<mount_point>/podman_storage/storage/graphroot"
    runroot = "<mount_point>/podman_storage/storage/runroot"
    </copy>
    ```

4. Create custom tmp directory for podman

    ```bash
    <copy>
    mkdir -p <mount_point>/podman_tmp
    </copy>
    ```

5. Run `vi ~/.config/containers/containers.conf` and paste below settings. This sets TMPDIR for podman to be the directory we just created with enough free space.

    ```bash
    <copy>
    [engine]
    env = ["TMPDIR=<mount_point>/podman_tmp"]
    </copy>
    ```

## Task 2: Get access to Oracle Container Registry

Oracle Container Registry is an online repository managed by Oracle that allows to store, share, and manage container images (such as Docker or Podman images). This platform is useful for the installation of the components Oracle AI Agent Studio.

1. Go to the [Oracle Container Registry website](https://container-registry.oracle.com/).

2. Login and generate auth token.

3. Login using key and username(email) from Oracle Container Registry by running the following command.

    ```bash
    <copy>
    podman login container-registry.oracle.com
    </copy>
    ```

## Task 3: Install podman-compose

Podman compose is a Podman tool that allows to run multi-container applications, such as Oracle AI Agent Studio.

1. Update python to 3.12

    ```bash
    <copy>
    sudo yum install python3.12 python3.12-pip
    </copy>
    ```

2. Install podman-compose

    ```bash
    <copy>
    python3.12 -m pip install podman-compose
    </copy>
    ```

## Task 4: Set Up Host for Persistent Services and Application Access

### Enable User Lingering

To ensure that Podman containers continue running even after the user logs out, you must enable linger mode for the user account that will deploy the container. This prevents the operating system from terminating all processes tied to the user’s session once it ends or becomes stale.

1. To check if linger is enabled for your user, run the following command:

    ```bash
    <copy>
    loginctl user-status <user> | grep -m1 Linger
    </copy>
    ```

    Expected output if linger is enabled:

    ```bash
    Linger: yes
    ```

2. If linger mode is not set, enable it for your user by running:

    ```bash
    <copy>
    loginctl enable-linger <user>
    </copy>
    ```

### Configure Network Firewall

By default, most Oracle Linux distributions restrict incoming network traffic for security reasons. Opening port 8080 in the firewall allows external clients to connect to the application hosted on this port, ensuring that authorized users can access the service while maintaining system security. For more information on securing network access, refer to the Oracle Cloud Infrastructure Network Security documentation.

1. Configure the firewalls to allow you access the application by running the following commands:

    ```bash
    <copy>
    sudo firewall-cmd --zone=public --permanent --add-port=8080/tcp
    sudo firewall-cmd --reload
    </copy>
    ```

## Acknowledgements

- **Author** - Emilio Perez, Member of Technical Staff, Database Applied AI
- **Last Updated By/Date** - Emilio Perez - August 2025
