# AI Workflow Coach – Multi-Agent Task Prioritization & Planning System

This project implements an **AI Workflow Coach** that automatically organizes daily work for small teams using a multi-agent architecture. The system analyzes tasks, detects blockers, scores priorities, identifies patterns in meeting notes, schedules time-blocks, integrates with Google Calendar, and sends personalized daily briefings via Slack.

---

## ✨ Key Features

### Multi-Agent Architecture
The system uses independent agents that each solve a piece of the workflow problem:

- **Priority Agent** – Computes urgency using delay, impact, effort, and risk.
- **Bottleneck Agent** – Detects blocked, overdue, or unassigned tasks.
- **Trend Analyzer** – Finds recurring issues like overwhelm or unclear requirements.
- **Delegation Agent** – Suggests load balancing and task reassignment.
- **Focus Agent** – Builds time-blocked schedules for each team member.
- **Calendar Agent** – Books focus sessions into Google Calendar.
- **Slack Notifier** – Sends each member a personalized “Daily Plan” briefing.

All agents are orchestrated by the central controller:  
**`EnhancedFallbackOrchestrator`**

---

## 📊 What the System Does Automatically

- Loads your team’s **tasks.csv** and **notes.csv**  
- Computes a **0–100 priority score** per task  
- Detects delays, blockers, and workload overload  
- Extracts emotional/operational signals from notes  
- Creates **top 3 tasks per team member**  
- Builds a **9–5 focus schedule**  
- Syncs focus blocks to **Google Calendar**  
- Sends a personalized briefing via **Slack**  
- Saves structured outputs for tracking progress  

---

## 🗂️ Output Structure

```txt
outputs/
 ├── demo_daily_coach_plan.json        # Final recommended tasks per team member
 ├── briefing_fallback_*.txt           # Slack fallback notifications (if API fails)
 ├── calendar_simulator.json           # In-memory calendar storage when GCal is off
 ├── events_log.json (optional)        # Session logs for debugging / analysis
```

# AI Workflow Coach
### Workflow / Architecture

<p align="center">
  <img width="500" alt="AI workflow " src="https://github.com/user-attachments/assets/3d61bade-c829-40fb-8c70-14b95b2d7690" />
</p>

### Slack Message
<p align="center">
  <img width="500" alt="Slack" src="https://github.com/user-attachments/assets/732861ad-cd74-4f58-806f-80166a1afd37" />
</p>

### Slack Schedule Focus Block
<p align="center">
  <img width="500" alt="Slack2" src="https://github.com/user-attachments/assets/ec63a086-2a7d-4dee-b732-3d5c7605757d" />
</p>

## 🚀 How to Run

1. Set environment variables (Slack + Google Calendar tokens if used).
2. Run all notebook cells.
3. Execute:
```
result = await enhanced_orch.daily_checkin(tasks_df, notes_df, session_id="daily_run")
```
4. View results on Slack or inside the outputs/ folder.
## 🧠 Why This Project Matters

Daily planning normally wastes time: choosing tasks, checking blockers, updating calendars, and writing status messages.
This AI Workflow Coach automates the entire workflow loop, freeing people to focus on real work instead of organization.

## 📌 Status

This is a functional submission for the Kaggle Agentic AI Workshop / Google ADK.
Future improvements may include adaptive memories, learned priority weights, and long-term workload modeling.
