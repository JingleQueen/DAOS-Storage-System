📘 My Learning Journey: DAOS, Docker, and Storage Systems

This document summarizes my hands-on learnings and implementation experience over the last month with DAOS (Distributed Asynchronous Object Storage), Docker/Kubernetes environments, and related storage and operating system concepts. It is meant to act as a structured knowledge base and portfolio entry for GitHub.

🔹 Topics I Learned

1. DAOS (Distributed Asynchronous Object Storage)

DAOS Installation & Setup

Built DAOS from source (v2.4 and v2.6 releases).

Installed dependencies, Go (>=1.21), and build system (scons).

Configured environment variables and added daos & dmg CLI tools to PATH.

Performed verification steps (daos version, dmg version).

DAOS Tools (daos & dmg)

Learned usage of dmg for cluster/system management.

Learned usage of daos for user-level pool/container operations.

DAOS Deployment on Docker

Built base DAOS images using docker-compose.yml.

Created DAOS server, admin, and client containers.

Worked with DAOS client to create pools and containers.

POSIX Integration (DFuse)

Mounted DAOS containers using dfuse.

Verified POSIX access with ls -l, df -h, and file operations.

TLS and Certificates in DAOS

Generated and configured DAOS certificates (gen_certificates.sh).

Configured daos_agent.yml, daos_server.yml, and daos_control.yml with transport layer security.

Error Handling and Fixes

Solved agent socket issues (/var/run/daos_agent/daos_agent.sock).

Fixed pool creation errors (ratio mismatches, duplicate labels).

Corrected certificate and path mismatches.

Learned about DER_MISC(-1025) and transport config debugging.

2. Docker & Kubernetes

Docker for DAOS

Used docker-compose to bring up DAOS server/client/admin environments.

Learned container networking for DAOS (access_points must not be localhost).

Configured storage mount points inside containers (/mnt/daos0, /mnt/daos1).

Container Management

Edited configs on host and mounted them into containers.

Used docker exec to run daos commands from inside the client.

Learned to regenerate CA certs and remount them into containers.

Kubernetes Perspective (Conceptual)

Explored how DAOS services can be mapped to Kubernetes pods.

Understood DAOS servers as StatefulSets, agents as DaemonSets, and control/admin as Deployments.

3. Storage Concepts

Object Storage vs POSIX Storage

Learned how DAOS supports both S3 (object) and POSIX (via DFuse) interfaces.

Worked with container creation in POSIX mode.

Pools and Containers

Understood pools as resource partitions (SCM + NVMe).

Containers as namespaces inside pools (with types like POSIX, HDF5, etc.).

Storage Ratios & Layouts

Learned about SCM:NVMe ratio during pool creation (--scm-ratio, --nvme-ratio).

Understood service ranks and pool label uniqueness.

Error Debugging in Storage

BIO errors (storage device mismatches) and how to align configs.

Network and CPU warnings and their impact on storage services.

4. Versity Gateway (S3 on DAOS)

Installed Versity Gateway on Linux.

Configured it to run in POSIX mode pointing to a DFuse mount.

Started S3 gateway on custom ports and tested connectivity.

Configured AWS CLI on both host and container to interact with S3 endpoint.

5. OS and Storage-Related Topics

Linux Filesystem Management

Created/mounted directories for DAOS storage.

Worked with df, ls, and debugging missing system tools (ip, ss).

Networking in Containers

Understood Docker internal networking and how to expose services.

Debugged connectivity using ping, ensuring correct syntax (ping -c).

Process & Service Management

Used systemctl, journalctl, and docker logs for service debugging.

Learned to stop/start DAOS management services using daos-cm.sh.

🚀 Implementation Flow I Learned

Build DAOS from source and verify CLI tools.

Deploy DAOS server/admin/client via Docker.

Configure certificates and secure communication.

Create pools and containers.

Mount DFuse for POSIX access.

Deploy Versity Gateway on top of DFuse mount.

Connect external clients (AWS CLI) to access DAOS via S3.

✅ Outcomes

Successfully installed and ran DAOS (v2.6) on Ubuntu.

Learned to manage DAOS pools, containers, and POSIX mounts.

Integrated DAOS with Docker containers for development.

Deployed Versity Gateway for S3 access on top of DAOS.

Gained practical knowledge of storage concepts, errors, and debugging.

📂 Next Steps

Explore Kubernetes-native deployment of DAOS.

Automate DAOS setup with Helm charts.

Benchmark DAOS performance for POSIX vs S3 workloads.

Learn about erasure coding, replication, and DAOS fault tolerance.

