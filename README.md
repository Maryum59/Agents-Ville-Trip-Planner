# Agents-Ville-Trip-Planner
# AgentsVille Trip Planner

An AI travel agent that plans a 3-day trip, checks its own work, fixes any mistakes, and only gives you the final answer when everything is perfect.

---

## What Is This?

Think of this project like hiring a very smart travel assistant.

You tell it:
- **Where** you want to go → AgentsVille
- **When** → August 15, 16, 17 (3 days)
- **What you enjoy** → Art, Technology, Street Food
- **Budget** → Maximum $500

The AI creates a full day-by-day plan. But here is the interesting part — before giving you the final answer, it checks the plan itself, finds any problems, fixes them, and only hands it over when it passes all 6 quality checks.

---

## The 2 Files in This Folder

### File 1 — `project_lib.py` (The City Data)

This file holds all the information about AgentsVille that the AI is allowed to use. Think of it as the city guidebook.

**Weather for the 3 days:**

| Day | Weather | Good for outdoors? |
|---|---|---|
| August 15 | Sunny, 75°F | Yes |
| August 16 | Partly Cloudy, 70°F | Yes (with a light jacket) |
| August 17 | Rainy, 65°F | No — stay indoors |

**12 activities available across the 3 days:**

*August 15:*
- Art Gallery Tour — $20 (indoors)
- Tech Meetup: AI in the City — FREE (indoors)
- Street Food Festival — $30 (outdoors)
- Sunset Rooftop Photography Walk — $15 (outdoors)

*August 16:*
- Cultural Heritage Museum — $15 (indoors)
- Rooftop Art Show — $25 (outdoors)
- AI Demo Day — $10 (indoors)
- AgentsVille Night Market — $20 (outdoors)

*August 17 (Rainy day — all activities are indoors):*
- Indoor Cooking Masterclass — $40
- Tech History Museum — $15
- Virtual Reality Art Experience — $25
- Jazz Lounge and Dinner — $50

This file also contains small helper tools the AI uses to ask questions like "What activities are on August 17?" or "What is the weather on August 16?"

---

### File 2 — `project_starter.ipynb` (The AI Brain)

This is the main notebook where everything happens. A notebook is like a document where you write and run code step by step and see the results right away.

It has 10 sections (cells). Here is what each one does in plain English:

---

## How the Project Works — Step by Step

### Step 1 — Connect to the AI
The notebook connects to a GPT model (the same type of AI behind ChatGPT) so it can have a conversation with it.

---

### Step 2 — Enter the Trip Details
The traveler's information is saved:
- Destination: AgentsVille
- Dates: August 15–17, 2025
- Interests: Art, Technology, Street Food
- Budget: $500

---

### Step 3 — Read the City Data
The AI reads the weather forecast and the list of all 12 available activities before making any plan.

---

### Step 4 — Create the First Draft Plan
The AI is given a set of instructions:
- Only pick activities from the official list (no making things up)
- Avoid outdoor activities on the rainy day
- Match the traveler's interests as much as possible
- Keep the total cost under $500
- Plan at least 2 activities per day

The AI writes out a full 3-day itinerary. This first draft might have mistakes — that's okay, the next steps fix them.

---

### Step 5 — Check the Plan Against 6 Rules
The plan is tested like a checklist. All 6 must pass:

| Rule | The Question It Asks |
|---|---|
| 1. Right city? | Did the AI plan the trip for AgentsVille? |
| 2. Right dates? | Are the 3 days actually August 15, 16, and 17? |
| 3. Within budget? | Is the total cost $500 or less? |
| 4. Only real activities? | Did the AI stick to the official activity list, or did it make something up? |
| 5. Weather makes sense? | Are outdoor activities only on sunny or cloudy days — not on the rainy day? |
| 6. Enough activities? | Does each day have at least 2 things to do? |

If even one rule fails, the plan is sent back for fixing.

---

### Step 6 — The AI Fixes Its Own Mistakes (The Loop)

This is the most interesting part of the project.

The AI goes into a thinking loop where it:
1. **Thinks** about what went wrong
2. **Takes an action** using one of its tools
3. **Sees the result**
4. **Repeats** until everything is correct

**The 4 tools the AI can use inside this loop:**

| Tool | What It Does |
|---|---|
| Calculator | Adds up activity costs to check the total |
| Activity Lookup | Shows what activities are available on a specific date |
| Run All 6 Checks | Tests the current plan against all 6 rules and shows what passed or failed |
| Submit Final Answer | Locks in the finished plan — can ONLY be used after all 6 rules pass |

The loop runs up to 12 rounds. Here is what it looks like in real life:

```
THINK:   "The total cost is $520 but the budget is $500.
          I need to find a cheaper activity for August 16."

ACTION:  Look up all activities available on August 16.

RESULT:  [Sees the list — AI Demo Day costs $10,
          Rooftop Art Show costs $25]

THINK:   "I'll swap the Rooftop Art Show for AI Demo Day.
          That saves $15 and the traveler likes tech anyway."

ACTION:  Update the plan. Run all 6 checks again.

RESULT:  All 6 rules pass!

ACTION:  Submit the final plan.
```

---

### Step 7 — Write a Travel Story
Once the final plan passes all checks, the AI writes a short travel story about the trip — vivid, exciting, like something from a travel magazine. For example:

*"Your AgentsVille adventure begins under a bright August sun at the contemporary Art Gallery, where local and international art blurs the line between tradition and innovation. Later that evening, the Street Food Festival fills the air with aromas from over 30 vendors..."*

---

## What You Get at the End

1. A complete 3-day itinerary that has passed all 6 quality checks
2. A fun travel narrative written about your trip

---

## How to Run This Project

**You need:**
- Python on your computer
- Jupyter Notebook
- An API key from the Vocareum course platform (or OpenAI)

**Install what's needed:**
```
pip install openai pydantic jupyter
```

**Open the notebook:**
```
jupyter notebook project_starter.ipynb
```

**Add your API key** in Cell 2 where it says `api_key="..."`

Then run each cell from top to bottom, one by one.
