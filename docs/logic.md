# Logic of the SMART POLE Framework

The SMART POLE framework is designed to eliminate the "guessing" that AI does when faced with vague context. By breaking down "context" into 9 distinct categories, we ensure every "atom" of information is placed exactly where the AI can process it most efficiently.

## Deep Dive into Categories

### 1. S - Style (The AI's Mask)
- **Concept**: The persona the AI wears.
- **Atoms**: "Cynical noir," "Helpful tutor," "Academic paper."
- **Logic**: Sets the vocabulary and syntactic structure of the *response*.

### 2. M - Mastery (The User's Level)
- **Concept**: Who is the user? What is their cognitive load capacity?
- **Atoms**: "Senior Architect (High context)," "5-year-old child (Low context)," "Intermediate knitter."
- **Logic**: Prevents "average" explanations by locking into a specific expertise tier for the *explanation*.

### 3. A - Aim (The Objective & Scorecard)
- **Concept**: The specific result and how it will be judged.
- **Atoms**: "Persuade a skeptic," "Summarize for a CEO," "Success = User feels confident."
- **Logic**: Gives the AI a success metric and evaluation criteria.

### 4. R - Resource (The Toolbox)
- **Concept**: What does the AI have to work with?
- **Atoms**: "Use only the attached PDF," "Budget: $0," "Equipment: One laptop."
- **Logic**: Prevents the AI from suggesting impossible or irrelevant solutions.

### 5. T - Time (The Schedule/Era)
- **Concept**: When is this happening, or how long should it take?
- **Atoms**: "Set in 1920s Paris," "Deadline: 2 hours," "Duration: 5-minute read."
- **Logic**: Grounds the response in a temporal context.

### 6. P - People (The Human Variable)
- **Concept**: Who is this for? What do they value? What are their internal beliefs?
- **Atoms**: "Audience: Busy parents," "Value: Efficiency over cost," "Persona: Introverted," "Belief: Sustainability is key."
- **Logic**: Adjusts the empathy and focus of the response to match the user's worldview.

### 7. O - Outline (The Skeleton & Scope)
- **Concept**: The structural constraints and what to *exclude*.
- **Atoms**: "3 acts," "Bullet points followed by a table," "Ignore backyard gardens," "Focus only on balcony."
- **Logic**: Controls the layout and density of the information.

### 8. L - Locale (The Setting)
- **Concept**: The physical or conceptual environment, broken down into 4 sub-dimensions:
    - **L1 - Industry/Domain**: Banking, Healthcare, E-commerce, etc.
    - **L2 - Geography/Region**: Vietnam, EU, USA, etc.
    - **L3 - Legal/Regulatory**: GDPR, HIPAA, PCI-DSS.
    - **L4 - Cultural/Social**: Local customs, user behavior norms.

- **Priority Logic**: The importance of these 4 dimensions shifts based on the Industry context.
    - **Banking**: Legal (L3) > Industry (L1) > Geo (L2) > Cultural (L4).
    - **Healthcare**: Legal (L3) > Industry (L1) > Cultural (L4) > Geo (L2).
    - **E-commerce**: Cultural (L4) > Geo (L2) > Industry (L1) > Legal (L3).
    - *General Rule*: Industry > Geo > Cultural > Legal.
    
- **Logic**: Ensures the advice is not just "technically" correct but "contextually" viable.

### 9. E - Example (The Anchor)
- **Concept**: A reference point for the AI to follow.
- **Insight**: **Snippet Power > Name Dropping**. It is better to provide a concrete 3-line example than to say "Write like Shakespeare."
- **Atoms**: "Use this JSON schema: {...}", "Structure like this paragraph: [Quote]".
- **Logic**: Provides a "one-shot" or "few-shot" pattern for the AI to emulate.

## The SP-Atom Principle
A prompt is not a block of text; it is a collection of **Atoms**. 
- An atom is **indivisible context**. 
- Adding an atom **decreases entropy** (uncertainty).
- Removing an atom **increases guesswork**.

## The SP-Flaw Principle
A flaw is an "empty bucket". If you don't fill the "Resource" bucket, the AI will reach into its general training data and grab a random resource. This leads to hallucinations or generic advice.

## Weighted Readiness Scoring (v3.0)
To scientifically measure prompt quality, we assign weights to categories based on their impact:

| Category | Weight | Role |
|---|---|---|
| **Aim / Outline** | **2.0** | **CORE**: Without these, the request is structureless. |
| **Locale** | **CONDITIONAL** | **CORE (2.0)** for Advisory/Discovery, **1.5** for Generative, **0.5** for Deterministic |
| **People / Mastery / Resource** | **1.5 / 1.0** | **CONTEXTUALIZER**: Defines the constraints and flavor. |
| **Time / Style / Example** | **0.5** | **ACCELERATOR**: Enhances quality but not mandatory for logic. |

### Task-Type Classification
The system automatically classifies requests into 5 types:

| Task Type | Keywords | Locale Requirement |
|-----------|----------|-------------------|
| **Deterministic** | solve, calculate, algorithm, parse | Optional (0.5) |
| **Generative** | write, create, design, build | Contextualizer (1.5) |
| **Advisory** | advise, recommend, should I, strategy | 🔴 **CORE (2.0)** |
| **Discovery** | brainstorm, explore, ideas, research | 🔴 **CORE (2.0)** |
| **Compliance** | legal, policy, GDPR, regulation | 🔴 **CORE (2.0)** |

**Threshold**: A prompt is considered "Master/Gemini-Ready" only when it achieves a score of **≥ 67%** AND all required Core categories are confirmed.
