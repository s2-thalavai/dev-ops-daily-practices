# dev-ops-daily-practices

## Docker:

To install Docker on system, the steps vary slightly depending on your operating system. Here's a streamlined guide for each platform:

WSL 2 enabled (for Home edition users)

🐧 For Linux (Ubuntu/Debian)
    
    🛠️ Install Docker Engine
    
        sudo apt update
        sudo apt install docker.io -y
        sudo systemctl start docker
        sudo systemctl enable docker
    
    🔍 Verify Installation
    
        docker --version
        sudo docker run hello-world
    
    To run Docker without sudo, add your user to the Docker group:
    
        sudo usermod -aG docker $USER

Then log out and back in.

## Docker Compose

Docker Compose is a powerful tool that simplifies the management of multi-container applications. 
Instead of manually starting each container with its own configuration, you define everything in a single docker-compose.yml file 
and launch your entire stack with one command. 

Here's a quick breakdown:

🧩 What Docker Compose Does
    
    Defines services: Each containerized service (e.g., web app, database, cache) is described in YAML.
    
    Manages networks and volumes: Automatically sets up communication and persistent storage.
    
    Orchestrates lifecycle: Start, stop, rebuild, and monitor services with simple commands.

📄 Sample docker-compose.yml

yaml
        
        version: '3.8'
        services:
          web:
            image: nginx:latest
            ports:
              - "80:80"
          app:
            build: .
            depends_on:
              - db
          db:
            image: postgres:14
            environment:
              POSTGRES_USER: user
              POSTGRES_PASSWORD: pass
              
🚀 Common Commands
        
        docker compose up – Start all services
        
        docker compose down – Stop and remove containers, networks, volumes
        
        docker compose build – Build images defined in the file
        
        docker compose logs – View logs from all services

### Steps to Install Docker Compose (Linux)
    
    1. Prerequisite: Docker Engine
       
        Make sure Docker is already installed:
        
            docker --version
    
    2. Download Docker Compose Plugin
    
            sudo curl -L "https://github.com/docker/compose/releases/download/v2.38.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
       
    This grabs the latest stable release from the official GitHub repo.
    
    4. Make It Executable
    
            sudo chmod +x /usr/local/bin/docker-compose
       
    6. Verify Installation
    
            docker-compose --version
       
    should see something like:
    
<img width="760" height="276" alt="image" src="https://github.com/user-attachments/assets/2cbf3b53-56fb-4d24-b184-1fa7e539fc31" />


==========================================================================================================

Powershell Command to send mail using Azure ACS SMTP Relay
    
    $Password = ConvertTo-SecureString -AsPlainText -Force -String 'your-smtp-password'
    $Cred = New-Object -TypeName PSCredential -ArgumentList 'ur-smtp-username@azurecomm.net', $Password
    
    Send-MailMessage -From 'your-smtp-username@azurecomm.net' `
    -To 'sivasankar.thalavai@gmail.com' `
    -Subject 'Test mail' `
    -Body 'test' `
    -SmtpServer 'smtp.office365.com' `
    -Port 587 `
    -Credential $Cred `
    -UseSsl


=====================================================================

Bash Shell Command to send mail using Azure ACS SMTP Relay

    sudo apt install swaks
    
    swaks --to s2.thalavai@gmail.com \
      --from your-smtp-username@azurecomm.net \
      --server smtp.office365.com \
      --port 587 \
      --auth LOGIN \
      --auth-user your-smtp-username@azurecomm.net \
      --auth-password 'your-smtp-password' \
      --tls \
      --header "Subject: Test mail" \
      --body "test"
  

=====================================================================
