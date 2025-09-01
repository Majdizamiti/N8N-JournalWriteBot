JournalWriteBot 🤖📊
An advanced n8n workflow that acts as an AI-powered research assistant for journalists. It processes queries via WhatsApp (text, audio, or image), fetches economic data from the World Bank, performs web research, and delivers a synthesized summary with source citations and a confidence level.

Features
Multi-Modal Input: Accepts text, audio messages, and images via WhatsApp.

Automated Data Fetching: Retrieves official economic indicators from the World Bank API.

Web Research: Identifies reputable online sources for journalistic research.

AI-Powered Analysis: Uses Groq's LLMs to analyze, compare, and synthesize data into a clear Markdown report.

Voice & Image Processing: Integrates with ElevenLabs for speech-to-text and Groq's LLaVA for image understanding.

Installation & Setup
Step 1: Configure the ngrok Tunnel
    1 . Download and install Docker Desktop from this link : https://docs.docker.com/desktop/setup/install/windows-install/
    2 . Create your Docker-Compose.yml
        version: '3.8'
services:
  n8n:
    image: docker.n8n.io/n8nio/n8n
    container_name: n8n
    restart: always
    ports:
      - "5678:5678"
    environment:
      N8N_HOST: localhost
      N8N_PORT: 5678
      WEBHOOK_URL: http://localhost:5678
      GENERIC_TIMEZONE: Europe/Vilnius
    volumes:
      - n8n_data:/home/node/.n8n

volumes:
  n8n_data:
    3 . Run it using command : docker-compose up -d
    4 . Visit localhost:5678 and create an account
    5 . Downloand ngrok from : https://ngrok.com/ and extract it
Step 2: Configure the n8n Container
    1 . Open docker desktop
    2 . Search for n8n image and run it
    3 . Create a container with these setting :
       set your container name
       set the host port
       set the volumes: 
           host path : the path in which include the docker-compose file
           container path : /home/node/.n8n
       set the environement variables:    
          Variable : N8N_COMMUNITY_PACKAGES_ALLOW_TOOL_USAGE
          Value : true
          Variable : N8N_EDITOR_BASE_URL
          Value : https://[your-static-domain].ngrok.app (from Ngrok dashboard Claim your free static domain)
          Variable : WEBHOOK_URL
          Value : Same value as N8N_EDITOR_BASE_URL
          Variable : NSN_DEFAULT_BINARY_DATA_MODE
          Value : filesystem
    4 . Run the Container
Step 3: Run n8n workflow
    1 . Open cmd
    2 . cd "the path in which include ngrok program"
    3 . to get the endpoint online follow the steps from : https://dashboard.ngrok.com/get-started/setup/windows
    4 . visit localhost:"your host port"
    5 . Download N8N Workflow.json
    6 . import it into n8n localhost
Step 4 : setup the web interface
    1 . Download index.html

    <img width="1365" height="717" alt="Capture d'écran 2025-08-30 104550" src="https://github.com/user-attachments/assets/4e1c8b63-9f2e-48c5-935a-b31edebd63ab" />
Navigate to your ngrok installation directory:
<img width="1086" height="427" alt="Capture d'écran 2025-08-28 155827" src="https://github.com/user-attachments/assets/cba4a08a-bf5e-49ae-b252-67b6a20a3f0b" />
<img width="1365" height="717" alt="Capture d'écran 2025-08-30 104550" src="https://github.com/user-attachments/assets/4e1c8b63-9f2e-48c5-935a-b31edebd63ab" />
<img width="1365" height="714" alt="Capture d'écran 2025-08-30 104821" src="https://github.com/user-attachments/assets/5b352989-738e-4919-bf73-747210d48d5c" />
<img width="1365" height="715" alt="Capture d'écran 2025-08-30 104905" src="https://github.com/user-attachments/assets/58419b03-6c4f-4dab-9c2c-3a56d554209d" />
<img width="1365" height="713" alt="Capture d’écran 2025-08-30 105027" src="https://github.com/user-attachments/assets/0ff7ad08-6a15-41e0-88dc-ce35ba92d728" />
