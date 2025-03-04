# osTicket Docker Setup

## Overview
This repository contains a **Docker-based setup** for osTicket, a powerful open-source ticketing system. The setup includes:
- **MariaDB (MySQL)** as the database.
- **osTicket** running in a Docker container.
- **Persistent storage** for database and ticket data.

## Technologies Used
- Docker
- Docker Compose
- osTicket
- MariaDB (MySQL)

## Getting Started
### Prerequisites
Make sure you have **Docker** and **Docker Compose** installed:
- [Docker Installation Guide](https://docs.docker.com/get-docker/)
- [Docker Compose Installation](https://docs.docker.com/compose/install/)

### Installation
1. **Clone this repository:**
   ```bash
   git clone https://github.com/your-username/osTicket-setup.git
   cd osTicket-setup
   ```

2. **Start osTicket using Docker Compose:**
   ```bash
   docker-compose up -d
   ```

3. **Access osTicket in your browser:**
   ```
   http://localhost:8080
   ```

### Database Configuration
During the osTicket installation, use these database credentials:
- **Database Host:** `db`
- **Database Name:** `osticket`
- **Username:** `osticket_user`
- **Password:** `osticket_pass`

### Stopping the Containers
To stop the osTicket setup:
```bash
docker-compose down
```

## Future Improvements
- Add SSL for secure connections
- Automate email configurations
- Deploy on a cloud service

## Contributing
Feel free to fork this repository and submit pull requests!

## License
This project is open-source under the MIT License.
