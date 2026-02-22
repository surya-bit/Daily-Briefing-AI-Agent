# 🤖 Daily Briefing AI Agent

An n8n multi-workflow orchestration system that delivers a personalized morning briefing via email. An orchestrator AI agent coordinates three specialized sub-agents to fetch calendar events, AI news, and weather — then compiles everything into a formatted HTML email.

---

## 📁 Project Structure

```
├── Daily Briefing Bot.json       # Orchestrator workflow
├── GetCalenderEvents.json        # Sub-agent: Google Calendar
├── GetNews.json                  # Sub-agent: AI News via Tavily
├── GetWeather Workflow.json      # Sub-agent: Weather + Pickleball check
└── README.md
```

---

## 🔧 Workflows

### 1. Daily Briefing Bot (Orchestrator)
The main workflow that coordinates all sub-agents. Uses an AI Agent node powered by OpenAI to call each sub-agent as a tool, synthesize the results, and send the final briefing as an HTML email via Gmail.

### 2. GetCalenderEvents
Fetches today's Google Calendar events. Returns a list of meetings scheduled for the day including time, attendees, and a brief description of each event.

### 3. GetNews
Fetches the latest AI news using the [Tavily](https://tavily.com) search API. Returns top headlines and summaries relevant to artificial intelligence.

### 4. GetWeather Workflow
Fetches current weather for **Little Elm, TX**. Checks wind speed at 5PM and flags whether conditions are suitable for pickleball. If wind exceeds 10 mph, the briefing includes a note that it is not ideal for playing pickleball.

## Orchestrator Workflow:
<img width="1606" height="627" alt="Workflow" src="https://github.com/user-attachments/assets/6c0aeed7-5bc4-4889-a050-608293904f91" />

## Email output:
<img width="1064" height="420" alt="image" src="https://github.com/user-attachments/assets/c6870ca8-7645-473d-b282-d7a207010d3c" />

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| [n8n](https://n8n.io) | Workflow automation |
| OpenAI GPT | AI orchestration and summarization |
| Google Calendar API | Fetch daily events |
| Tavily API | AI news search |
| Open-Meteo / Weather API | Weather data |
| Gmail | Send daily briefing email |

---

## 🚀 Setup Instructions

### Prerequisites
- n8n instance (cloud or self-hosted)
- OpenAI API key
- Google Calendar OAuth credentials
- Tavily API key
- Gmail OAuth credentials

### Import Workflows
1. Open your n8n instance
2. Go to **Workflows → Import from file**
3. Import each `.json` file separately
4. Start with the sub-agent workflows first, then the orchestrator

### Configure Credentials
In each workflow, update the following credentials:
- **OpenAI** — Add your OpenAI API key
- **Google Calendar** — Connect your Google account via OAuth
- **Tavily** — Add your API key in the HTTP Request node body
- **Gmail** — Connect your Google account via OAuth

### Activate
1. Open each sub-agent workflow and click **Publish**
2. Open the **Daily Briefing Bot** orchestrator
3. Set your preferred trigger (Schedule Trigger recommended for daily delivery)
4. Toggle the workflow **Active**

---

## ⚠️ Notes

- Remove or blank out any API keys before sharing or committing this project
- The GetCalenderEvents workflow name has a typo ("Calender" instead of "Calendar") — keep it consistent when referencing it in the orchestrator tool call
- Tavily requires the API key passed in the **request body**, not the headers

---

## 📬 Sample Output

The daily briefing email includes:
- 📅 Today's calendar events with attendees and descriptions
- 📰 Top AI news headlines with links
- 🌤️ Current weather in Little Elm, TX
- 🏓 Pickleball suitability based on 5PM wind speed

---
