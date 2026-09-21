# Day 1 — Lab: Chatbot vs Rule-Based Workflow vs AI Agent

This is the **training / lab exercise** from *Agentic AI: Foundations and
Open-Source Practice — Day 1 Lab Manual*. It sets up a Python environment in
VS Code, connects it to an open LLM, and implements and compares a plain
chatbot, a rule-based workflow, and a tool-using AI agent on the same
scenario: private college course fees (CS101, AI202, DS303) that no public
LLM has seen.

## Project layout

```
day 1/
 |- .env.example     <- copy to .env and fill in your provider/key
 |- requirements.txt
 |- config.py          <- settings, provider selection, and the course-fee data
 |- check_setup.py     <- run first: tests the LLM connection
 |- chatbot.py          <- System 1: plain LLM chatbot
 |- workflow.py          <- System 2: rule-based workflow (no LLM)
 |- tools.py              <- tools available to the agent
 |- agent.py               <- System 3: AI agent (LLM + Tools + Loop)
 |- challenge.py            <- a question none of the systems was designed for
```

## Setup

1. Create and activate a virtual environment, then install dependencies:
   ```
   python -m venv .venv
   source .venv/bin/activate      # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```
2. Copy `.env.example` to `.env` and fill in the provider you're using
   (Ollama locally, or a free Groq / Hugging Face key).
3. Run `python check_setup.py` first to confirm the model connection works.
4. Run each system: `python chatbot.py`, `python workflow.py`,
   `python agent.py`, `python challenge.py`.

## What this lab demonstrates

- The **chatbot** answers fluently but hallucinates the private fee data it
  was never given.
- The **workflow** is exactly right, every time, for the two question
  shapes it has rules for, and fails cleanly outside them.
- The **agent** reasons about which tool to call, uses `get_course_fee` and
  `calculator` to ground its answers in the real data, and can handle
  question phrasings the workflow can't — at the cost of some run-to-run
  variability.

See the separate assessment repository for the graded scenario analysis.
