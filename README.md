TriageAI – Intelligent Email Triage RL Environment
📌 Overview

TriageAI is a Reinforcement Learning (RL) environment built using FastAPI and the OpenEnv specification. It simulates real-world email triage workflows where an AI agent must analyze incoming emails and decide the most appropriate action.

The environment is designed for training, evaluating, and benchmarking RL agents on email management tasks such as:

📩 Replying to customer queries
🚨 Escalating critical issues
📁 Archiving low-priority emails
❓ Requesting additional information
🚀 Features
OpenEnv-compatible RL environment
FastAPI-based REST API
Multiple difficulty levels
Task-specific grading functions
Reward-based evaluation
Docker support
Easy integration with RL agents
Health monitoring endpoints
🏗️ Project Architecture
TriageAI/
│
├── app.py              # FastAPI server
├── env.py              # Email RL Environment
├── tasks.py            # Task definitions
├── graders.py          # Reward functions
├── models.py           # Pydantic models
├── inference.py        # Agent inference logic
├── requirements.txt
├── Dockerfile
└── server/
    └── app.py
🎯 Available Actions

The agent can choose one of four actions:

Action	Description
reply	Respond directly to the email
escalate	Forward to a higher authority/team
archive	Store without further action
request_info	Ask for additional details
📚 Task Categories
Easy Tasks
Customer Queries
Newsletter Archiving
Medium Tasks
Billing Disputes
Return Policy Clarification
Hard Tasks
Server Outages
Security Data Breaches
📝 Example Tasks
Customer Query
{
  "email_text": "What are your working hours?",
  "sender": "customer",
  "urgency": 2
}

✅ Correct Action: reply

Security Breach
{
  "email_text": "Data breach detected, immediate action required!",
  "sender": "security",
  "urgency": 10
}

✅ Correct Action: escalate

⚙️ Installation
Clone Repository
git clone https://github.com/yourusername/TriageAI.git
cd TriageAI
Create Virtual Environment
python -m venv venv
Activate Environment

Linux/Mac

source venv/bin/activate

Windows

venv\Scripts\activate
Install Dependencies
pip install -r requirements.txt
▶️ Running the Server
uvicorn app:app --reload

Server starts at:

http://localhost:8000

API Documentation:

http://localhost:8000/docs
🔌 API Endpoints
Root
GET /

Returns environment information.

Health Check
GET /health

Response:

{
  "status": "ok",
  "environment": "email_triage_env"
}
List Tasks
GET /tasks

Returns all available tasks with grader information.

Reset Environment
POST /reset

Request:

{
  "task_id": "easy"
}
Execute Action
POST /step

Request:

{
  "task_id": "easy",
  "action_type": "reply"
}

Response:

{
  "reward": 0.95,
  "done": true
}
🎮 RL Workflow
Reset Environment
        │
        ▼
 Receive Observation
        │
        ▼
 Agent Selects Action
        │
        ▼
 Environment Evaluates
        │
        ▼
 Reward Generated
        │
        ▼
 Episode Ends / Continue
🏆 Reward System

The environment uses task-specific grading functions.

High Reward
Correct action selection
Appropriate urgency handling
Low Reward
Incorrect response
Delayed escalation
Misclassification

Reward Range:

0.01 → 0.99
🐳 Docker Deployment

Build Image:

docker build -t triageai .

Run Container:

docker run -p 8000:8000 triageai
💡 Use Cases
Reinforcement Learning Research
Email Automation Systems
Customer Support AI
Helpdesk Optimization
Multi-Agent Training
OpenEnv Benchmarking
🔮 Future Improvements
Multi-step conversations
Email attachments support
LLM-powered reasoning
Custom task creation
Priority prediction models
Real-world email datasets
Analytics dashboard
🛠️ Tech Stack
Python
FastAPI
Pydantic
OpenEnv
Docker
Reinforcement Learning
👨‍💻 Author

Ojashwee Kumar

B.Tech CSE | AI & ML Enthusiast

"Building intelligent systems that make decision-making faster, smarter, and more reliable." 🚀

📄 License

This project is licensed under the MIT License. Feel free to use, modify, and contribute.
