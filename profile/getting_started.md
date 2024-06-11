# Getting Started with pgShield 🚀

Welcome to pgShield, a Rust-based PostgreSQL load balancer with caching and broker capabilities. This guide will help you get up and running with pgShield quickly by using prebuilt binaries or container images.

## Table of Contents 📑

- [Prerequisites](#prerequisites) ✅
- [Installation](#installation) 🛠️
  - [Download Prebuilt Binaries](#download-prebuilt-binaries) 📦
  - [Using Container Images](#using-container-images) 🐳
- [Configuration](#configuration) ⚙️
- [Running pgShield](#running-pgshield) 🚦
- [Basic Usage](#basic-usage) 📋
- [Troubleshooting](#troubleshooting) 🛠️
- [FAQ](#faq) ❓

## Prerequisites ✅

Before you begin, ensure you have the following:

- PostgreSQL server 🐘
- Git 🌐 (if you plan to clone the repository)

## Installation 🛠️

### Download Prebuilt Binaries 📦

Prebuilt binaries for Windows, Linux, and macOS will be available soon. You can download them from the [releases page](https://github.com/pgShield/pgShield/releases).

1. **Windows**: Download the `pgShield-windows.zip` file, unzip it, and run the executable.
2. **Linux**: Download the `pgShield-linux.tar.gz` file, extract it, and run the binary.
3. **macOS**: Download the `pgShield-macos.tar.gz` file, extract it, and run the binary.

### Using Container Images 🐳

Container images for pgShield will be available soon. You can pull the image from Docker Hub and run it using the following commands:

```sh
docker pull pgshield/pgshield:latest
docker run -d -p 8080:8080 -v /path/to/config.json:/app/config.json pgshield/pgshield:latest
```

## Configuration ⚙️

Create a configuration file `config.json` in the directory where you will run pgShield. Below is an example configuration:

```json
{
  "postgresql_hosts": [
    {
      "host": "localhost:5432",
      "admin_auth_type": "trust"
    },
    {
      "host": "example.com:5432",
      "admin_auth_type": "password",
      "admin_username": "postgres",
      "admin_password": "mypassword"
    },
    {
      "host": "ldap.example.com:5432",
      "admin_auth_type": "ldap",
      "admin_username": "admin",
      "admin_password": "ldappassword"
    },
    {
      "host": "cert.example.com:5432",
      "admin_auth_type": "cert",
      "admin_username": "cert_user",
      "admin_password": "certpassword"
    }
  ],
  "listen_port": "8080",
  "max_conns": 100,
  "cache_ttl": 3600,
  "health_check_interval": 60,
  "replication_mode": false,
  "query_cache_ttl": 600,
  "logging": {
    "log_to_file": true,
    "log_to_console": true,
    "log_to_syslog": false,
    "log_dir": "/var/log/pgShield",
    "syslog_facility": "LOG_USER",
    "syslog_process_name": "pgShield"
  }
}
```

## Running pgShield 🚦

### Using Prebuilt Binaries

1. Ensure your `config.json` file is in the same directory as the pgShield binary.
2. Run the binary:

   ```sh
   ./pgShield
   ```

### Using Docker

1. Ensure your `config.json` file is accessible to Docker.
2. Run the container:

   ```sh
   docker run -d -p 8080:8080 -v /path/to/config.json:/app/config.json pgshield/pgshield:latest
   ```

## Basic Usage 📋

Once pgShield is running, it will listen for incoming requests on the port specified in your configuration (e.g., 8080). You can interact with pgShield using any PostgreSQL client by connecting to `localhost:8080` or the appropriate host and port if running remotely.

## Troubleshooting 🛠️

If you encounter issues, here are some common troubleshooting steps:

- **Check Logs**: Ensure logging is enabled and check the log files located in the directory specified in `log_dir`.
- **Verify Configuration**: Double-check your `config.json` for any syntax errors or incorrect values.
- **Database Connectivity**: Ensure your PostgreSQL servers are running and accessible from the pgShield server.

## FAQ ❓

**Q: How do I add a new PostgreSQL host to the configuration?**
A: Add a new object to the `postgresql_hosts` array in the `config.json` file with the appropriate connection details.

**Q: Can I use pgShield with other databases?**
A: Currently, pgShield is designed to work with PostgreSQL databases. Support for other databases may be considered in future versions.

**Q: How do I contribute to pgShield?**
A: Contributions are welcome! Please refer to the [Contributing](https://github.com/pgShield/pgShield/blob/main/CONTRIBUTING.md) guidelines in the repository for more information.

---

For more details and the latest updates, visit the [pgShield website](https://pgshield.github.io). If you have any questions or need further assistance, please contact us via [GitHub](https://github.com/ilstarno) or [LinkedIn](https://www.linkedin.com/in/indrit-z-3b6b8ba6/).