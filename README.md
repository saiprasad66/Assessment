# Yii2 App Deployment on Docker Swarm (AWS EC2)

## Setup Instructions

1. Launch AWS EC2 (Ubuntu 20.04 preferred).
2. Clone this repository into your local machine.
3. Edit Ansible `inventory` file with your EC2 public IP and SSH key path.
4. Run:

   ```bash
   cd ansible
   ansible-playbook -i inventory playbook.yml
   ```

5. Push any code changes to `main` branch to trigger CI/CD via GitHub Actions.

## Assumptions

- You are using Docker Hub for images.
- GitHub Secrets are configured:
  - `DOCKER_USERNAME`
  - `DOCKER_PASSWORD`
  - `EC2_HOST`
  - `EC2_USER`
  - `EC2_SSH_KEY`
  
## How to Test Deployment

- Access: `http://your-ec2-public-ip/`
- Service is exposed via NGINX reverse proxy to the Docker container running Yii2 app.

## Notes

- Health checks can be added to `docker-compose.yml` under the `services` block.
- Monitoring can be enhanced via Prometheus + Node Exporter.
