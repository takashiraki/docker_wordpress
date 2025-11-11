# Docker WordPress

A Docker-based WordPress development environment with SSL/TLS support using Let's Encrypt.

## Features

- WordPress latest version
- SSL/TLS support with Let's Encrypt
- Environment variable configuration
- Multi-network setup (proxy, infrastructure, and WordPress networks)
- Dev container support for development

## Prerequisites

- Docker
- Docker Compose
- External networks: `my_proxy_network` and `my_infra_network` must be created beforehand

## Quick Start

1. Clone this repository:
   ```bash
   git clone <repository-url>
   cd sample_wordpress
   ```

2. Copy the example environment file and configure it:
   ```bash
   cp .env.example .env
   ```

3. Edit `.env` file with your settings:
   ```bash
   MY_WORDPRESS_DB=your_database_name
   VIRTUAL_HOST=your-domain.com
   LETSENCRYPT_EMAIL=your-email@example.com
   ```

4. Start the WordPress container:
   ```bash
   docker-compose up -d
   ```

5. Access your WordPress site at the configured domain.

## Environment Variables

| Variable                | Description                | Default             |
| ----------------------- | -------------------------- | ------------------- |
| `MY_WORDPRESS_HOST`     | Database host              | `my_database`       |
| `MY_WORDPRESS_DB`       | Database name              | (required)          |
| `MY_WORDPRESS_USER`     | Database user              | `root`              |
| `MY_WORDPRESS_PASSWORD` | Database password          | `rootpw`            |
| `VIRTUAL_HOST`          | Domain name for the site   | (required)          |
| `LETSENCRYPT_HOST`      | Domain for SSL certificate | `${VIRTUAL_HOST}`   |
| `LETSENCRYPT_EMAIL`     | Email for Let's Encrypt    | `hello@example.com` |
| `LETSENCRYPT_TEST`      | Use Let's Encrypt staging  | `true`              |
| `CERT_NAME`             | Certificate name           | `default`           |

## Network Configuration

This setup uses three Docker networks:
- `my_wordpress_network`: Internal WordPress network
- `my_proxy_network`: External proxy network (must be created beforehand)
- `my_infra_network`: External infrastructure network (must be created beforehand)

To create the external networks:
```bash
docker network create my_proxy_network
docker network create my_infra_network
```

## Development

This project includes a dev container configuration for development. Open the project in VS Code with the Dev Containers extension to get started.

## File Structure

```
.
├── docker-compose.yml    # Docker Compose configuration
├── .env.example          # Example environment variables
├── .devcontainer/        # Dev container configuration
└── wordpress/            # WordPress files (mounted volume)
```

## License


This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
