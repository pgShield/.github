# pgShield 🛡️

pgShield is a Rust-based PostgreSQL load balancer with caching and broker capabilities, designed to handle 20,000 requests per minute. It aims to optimize PostgreSQL performance and security by managing multiple databases from various locations as one and providing enhanced client services beyond traditional socket pooling.

## Table of Contents 📑

- [Features](#features) ✨
- [Getting Started](#getting-started) 🚀
  - [Prerequisites](#prerequisites) ✅
  - [Installation](#installation) 🛠️
  - [Configuration](#configuration) ⚙️
  - [Usage](#usage) 📋
- [Contributing](#contributing) 🤝
- [License](#license) 📜
- [Contact](#contact) 📞

## Features ✨

- High-performance load balancing ⚖️
- Caching for improved query response times ⚡
- Broker capabilities for efficient database management 🗄️
- Supports handling multiple databases as a single entity 🗃️
- Enhanced security and optimization for PostgreSQL 🔒

## Getting Started 🚀

For detailed instructions on getting started, please refer to the [Getting Started Guide](GETTING_STARTED.md).

### Prerequisites ✅

Before you begin, ensure you have the following:

- Rust and Cargo installed 🦀
- PostgreSQL server 🐘
- Git 🌐

### Installation 🛠️

1. Clone the repository:

   ```sh
   git clone https://github.com/pgShield/pgShield.git
   cd pgShield
   ```

2. Build the project:

   ```sh
   cargo build --release
   ```

### Configuration ⚙️

Create a configuration file `config.json` in the project root directory. Below is an example configuration:

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

### Usage 📋

Run pgShield with the following command:

```sh
cargo run --release
```

This will start the pgShield server, which will begin balancing requests across your configured PostgreSQL databases.

## Contributing 🤝

Contributions are welcome! Please follow these steps to contribute:

1. Fork the repository 🍴
2. Create a new branch (`git checkout -b feature-branch`) 🌿
3. Make your changes and commit them (`git commit -m 'Add some feature'`) 💬
4. Push to the branch (`git push origin feature-branch`) 🚀
5. Create a new Pull Request 📬

We are particularly looking for contributions in the following areas:

- Documentation 📝
- Website creation 🌐
- New ideas and feature suggestions 💡

For more details, please see our [Contributing Guidelines](CONTRIBUTING.md).

## License 📜

This project is licensed under the MIT License. See the [LICENSE](LICENSE.md) file for details.

## Contact 📞

For any inquiries, please contact:

- GitHub: [ilstarno](https://github.com/ilstarno) 💻
- LinkedIn: [Indrit Z](https://www.linkedin.com/in/indrit-z-3b6b8ba6/) 🔗

Follow the project on our [website](https://pgshield.github.io) for the latest updates and instructions for building, installing, configuring, and using pgShield to optimize your PostgreSQL infrastructures.

