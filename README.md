# Doubt Desk 📚
### A Multi Agent AI Learning Assistant Built with Switch and OpenAI Codex

## About the Project

Doubt Desk is an AI powered collaborative learning assistant inspired by my experience as a tutor.

As a tutor, my teaching workflow usually follows four stages: explaining a concept, testing the student's understanding, evaluating their answers, and summarizing the important points for revision.

I wanted to recreate this exact workflow using multiple AI agents instead of relying on a single chatbot.

Doubt Desk brings four specialized AI agents into one shared room using Switch. Each agent has a specific responsibility, and together they create an interactive learning experience for students.

## The Problem

Most AI learning tools focus on answering questions. However, learning does not stop at understanding an explanation.

Students also need opportunities to practice, receive feedback, identify mistakes, and revise what they have learned.

Doubt Desk addresses this by bringing these stages together through a coordinated multi agent workflow.

## The Four AI Agents

| Agent | Responsibility | How it is triggered |
| :--- | :--- | :--- |
| Tutor | Explains concepts in three simple steps with an everyday analogy. | @tutor |
| Quizzer | Generates two practice questions and evaluates the student's answers. | @quizzer |
| Summarizer | Produces a three line learning recap. | @summarizer |
| Mindmapper | Generates a visual SVG mind map with four to six branches. | @mindmapper |

### 1. Tutor

The Tutor explains a requested topic in exactly three simple steps and includes one everyday analogy to make the concept easier to understand.

After explaining, it hands off the topic to the Quizzer by sending a message in the shared room.

### 2. Quizzer

The Quizzer generates exactly two short practice questions based on the Tutor's explanation.

It waits for the student to submit answers, evaluates both responses, identifies mistakes, and provides corrections.

After evaluating the answers, it requests the Summarizer to generate a recap.

### 3. Summarizer

The Summarizer reviews the conversation and produces exactly three lines:

1. Topic: The topic discussed.
2. Key idea: The main concept explained.
3. Quiz: The student's performance.

It only uses information available in the conversation and does not guess unanswered quiz results.

### 4. Mindmapper

The Mindmapper creates a standalone SVG mind map for a requested topic.

It places the main topic at the center and creates four to six branches with useful labels, clear colors, and readable text.

The generated SVG is saved as a file and shared back in the same Switch room.

## How Switch Powers Doubt Desk

Switch acts as the coordination environment for the four specialized agents.

I used OpenAI Codex as the connected coding agent and Switch Console to configure and manage the agents.

The agents operate in a shared room called Doubt Desk. Users interact with them through @mentions, while agents can address other agents to request the next task.

The workflow is designed around agent collaboration rather than isolated chatbot interactions.

## Learning Workflow

The intended learning sequence is:

**Step 1: Explanation**

The student sends:

`@tutor Explain binary search.`

The Tutor explains binary search in three simple steps and provides an everyday analogy.

**Step 2: Practice**

The Tutor hands the topic to the Quizzer.

The Quizzer generates two short questions and waits for the student's answers.

**Step 3: Evaluation**

The student replies by mentioning the Quizzer:

`@quizzer My answers: 1) ... 2) ...`

The Quizzer checks both answers and explains any mistakes.

**Step 4: Revision**

The Quizzer requests the Summarizer to provide a three line recap.

**Step 5: Visualization**

The student can request a mind map separately:

`@mindmapper Make a mind map of binary search.`

The Mindmapper generates an SVG file and shares it in the room.

## Technology and Tools

| Technology | Purpose |
| :--- | :--- |
| Switch | Multi agent coordination |
| Switch Console | Agent and room management |
| OpenAI Codex | Connected coding agent |
| Docker Desktop | Running the local Switch environment |
| SVG | Visual mind map generation |

## Setup and Reproduction

To explore or recreate Doubt Desk:

1. Install Docker Desktop.
2. Download and install Switch Console from the Switch repository releases.
3. Launch Switch Console and allow the local Switch server to start.
4. Sign in and configure the connected Codex agent.
5. Use switch buddy to create the four specialized agents.
6. Configure each agent using the instructions provided in `agent-instructions.md`.
7. Create a shared room named `doubt-desk`.
8. Add the Tutor, Quizzer, Summarizer, and Mindmapper agents to the room.
9. Test the workflow using the example prompts above.

**Switch Repository:** https://github.com/sandbox-quantum/switch

## Project Structure

```text
doubt-desk/
│
├── README.md
├── agent-instructions.md
├── screenshots/
│   ├── switch-console.png
│   ├── agent-workflow.png
│   └── mindmap.png
│
└── demo-link.txt
```

## Screenshots

Screenshots of the Switch Console, shared agent room, and generated mind map will be included here.

## Demo

[Add your demonstration video link here]

## What I Learned

Building Doubt Desk helped me understand that multi agent systems are not simply about creating multiple AI assistants.

Each agent needs clear responsibilities, instructions, and a defined role in the overall workflow.

I also learned the importance of testing agent interactions, debugging communication issues, and designing workflows around real user needs.

Most importantly, I enjoyed turning a teaching process I already use as a tutor into a collaborative AI system.

## Future Improvements

1. Improve the reliability of communication and handoffs between agents.
2. Add better visibility into agent activity and execution status.
3. Explore more interactive learning features.
4. Extend the workflow to support additional subjects and learning requirements.

---

**Built with curiosity, inspired by teaching, and powered by Switch.**