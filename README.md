#README.md

# Simple Nginx Website with Docker

## Requirements
1. Add Docker's official GPG key:
   ```bash
   sudo apt-get update
   sudo apt-get install ca-certificates curl
   sudo install -m 0755 -d /etc/apt/keyrings
   sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
   sudo chmod a+r /etc/apt/keyrings/docker.asc
   ```
   
2. Add the repository to Apt sources:
   ```bash
   echo \
     "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
     $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
     sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   sudo apt-get update
   ```
   
3. Install Docker:
   ```bash
    sudo apt-get install docker-ce docker-ce-cli containerd.io
   ```

4. Test Docker's version & running:
   ```bash
   sudo systemctl enable docker
   sudo systemctl start docker
   sudo docker version
   sudo docker run hello-world
   ```
   

## Steps to Build and Run

1. Build the Docker image:
   ```bash
   sudo docker build -t html-nginx:1.0 .
   ```

2. Run the container:
   ```bash
   sudo docker run -d -p 8080:8080 --name simple-nginx html-nginx:1.0
   ```

3. Visit `http://<your-ip>:8080` to see the website.

## Security
- Access is restricted to the IP `192.168.56.129`.

## Troubleshooting
- Use `sudo docker logs simple-nginx` to check logs.
