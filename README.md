# Trino HDFS Setup

This project provides a Docker-based setup for running Trino with HDFS and Hive Metastore. It includes all necessary components for a complete data lake setup.

## Components

- **Trino**: Distributed SQL query engine
  - Coordinator node
  - Worker node
- **HDFS**: Hadoop Distributed File System
  - NameNode
  - DataNode
- **Hive Metastore**: Metadata management service
- **MySQL**: Database for Hive Metastore

## Prerequisites

- Docker
- Docker Compose
- At least 8GB of RAM
- At least 20GB of disk space

## Configuration

The project uses environment variables defined in `.env` file for configuration. Key variables include:

- `TRINO_VERSION`: Version of Trino to use
- `HADOOP_VERSION`: Version of Hadoop/HDFS
- `HIVE_VERSION`: Version of Hive Metastore
- `MYSQL_VERSION`: Version of MySQL

## Getting Started

1. Clone the repository:

   ```bash
   git clone https://github.com/luradata/trino-hdfs-setup.git
   cd trino-hdfs-setup
   ```

2. Start the services:

   ```bash
   docker-compose up -d
   ```

3. Wait for all services to be healthy. You can check the status using:

   ```bash
   docker-compose ps
   ```

## Accessing the Services

- **Trino Web UI**: <http://localhost:8080>
- **HDFS Web UI**: <http://localhost:9870>
- **Hive Metastore**: localhost:9083
- **MySQL**: localhost:3306

## Default Credentials

- **Trino**:
  - Username: admin
  - Password: admin
- **MySQL**:
  - Username: hive
  - Password: hive
  - Database: metastore_db

## Directory Structure

```
.
├── docker-compose.yml    # Docker Compose configuration
├── .env                 # Environment variables
├── hadoop/             # HDFS configuration and data
├── hive-metastore/     # Hive Metastore configuration
├── hive-mysql/         # MySQL data
└── trino/             # Trino configuration and data
```

## Security Notes

- This setup is configured for development purposes with basic security settings
- For production use:
  - Set `TRINO_AUTHENTICATION_ALLOW_INSECURE_OVER_HTTP=false`
  - Change default passwords
  - Configure SSL/TLS
  - Implement proper authentication mechanisms

## Troubleshooting

1. Check service logs:

   ```bash
   docker-compose logs <service-name>
   ```

2. Verify service health:

   ```bash
   docker-compose ps
   ```

3. Common issues:
   - Port conflicts: Ensure required ports are not in use
   - Memory issues: Adjust JVM settings in respective config files
   - Network issues: Check if all containers are on the same network

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the terms specified in the [LICENSE](./LICENSE) file.
