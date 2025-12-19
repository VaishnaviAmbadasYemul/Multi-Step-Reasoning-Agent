# Multi-Step-Reasoning-Agent

## Overview

This project implements a Multi-Step Reasoning Agent that solves structured word problems using a Planner → Executor → Verifier architecture.

The agent:

Breaks problems into steps internally

Executes calculations programmatically

Verifies correctness before responding

Returns results in a fixed JSON schema

Avoids exposing full chain-of-thought to the user

Problem Types Supported

Time difference calculations

Arithmetic reasoning (counts, totals)

Constraint-based slot selection

Example:

“If a train leaves at 14:30 and arrives at 18:05, how long is the journey?”


Project Structure
reasoning-agent/
│
├── agent.py        # Core agent logic (CLI)
├── app.py          # Streamlit UI (optional interface)
├── tests.py        # Test suite with example logs
├── README.md       # Documentation
└── requirements.txt (optional)


Agent Architecture

The agent is divided into three mandatory internal phases:

1️⃣ Planner

Reads the user question

Produces a concise internal plan
Example:
parse → extract quantities → compute → verify → format

2️⃣ Executor

Executes the plan step by step

Performs calculations using Python

Produces intermediate results

3️⃣ Verifier

Re-checks the solution

Validates constraints (e.g., non-negative values, valid durations)

Triggers retry or failure if validation fails

**How to Run**

1️⃣ Start the app
streamlit run agent.py

2️⃣ Open in browser
http://localhost:8501

## Prompt Design (Conceptual)

Separate prompts are designed for:

Planner Prompt

“Given a word problem, produce a numbered step-by-step plan.”

Executor Prompt

“Given a plan and question, follow steps and compute intermediate values.”

Verifier Prompt

“Check if the proposed solution is consistent and valid.”

(LLM calls are mocked for simplicity but are easily replaceable.)
