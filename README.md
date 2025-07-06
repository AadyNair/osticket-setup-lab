# osTicket Helpdesk Setup on AWS EC2

This project documents the setup of an open-source helpdesk system (osTicket) on an Amazon EC2 instance using a LAMP stack (Linux, Apache, MariaDB, PHP).

## Environment

- **OS**: Amazon Linux 2023 (EC2 t2.micro)
- **Web Server**: Apache
- **Database**: MariaDB 10.6 (from official repo)
- **PHP**: PHP 8.1+ with necessary extensions
- **App**: osTicket v1.18.1

## Steps Completed

### 1. EC2 Instance Setup
- Created key pair and connected via SSH
- Secured `.pem` file with `chmod 400`
- Updated OS with `sudo dnf update -y`

### 2. Installed LAMP Stack
- Apache: `sudo dnf install httpd -y`
- PHP and extensions: `sudo dnf install php php-mysqlnd php-gd php-mbstring php-xml php-intl php-cli -y`
- MariaDB: Added official repo and installed MariaDB 10.6

### 3. Database Setup
```sql
CREATE DATABASE osticket;
CREATE USER 'osticketuser'@'localhost' IDENTIFIED BY 'StrongPass123!';
GRANT ALL PRIVILEGES ON osticket.* TO 'osticketuser'@'localhost';
FLUSH PRIVILEGES;

