# The Car Whisperer 

## Overview

**The Car Whisperer** is an intelligent conversational application that recommends ideal cars to users based on their preferences. Built using Streamlit and LangChain with structured prompts and schema definitions, the app utilizes LLM capabilities (via Groq's LLaMA 3.1 model) to extract user intent and return high-quality, tailored car recommendations.

---

## Problem Statement

Car buyers often struggle with decision fatigue due to the vast number of options and lack of expert advice tailored to their needs. Traditional recommendation systems are either static, filled with ads, or require manual filter tuning.

---

## Our Solution

**The Car Whisperer** offers a conversational interface that extracts nuanced preferences (budget, type, features) and uses an LLM to dynamically suggest vehicles best suited to the user's needs. It simplifies the research phase, making the car-buying journey informed, fast, and engaging.

---

## Key Features

| Feature                        | Description |
|-------------------------------|-------------|
| **Conversational UI**         | Users type preferences in natural language (e.g., “I want a hybrid SUV under $30k”) |
| **Intelligent Extraction**    | Uses a prompt chain to identify budget, car type, and features |
| **AI-Powered Recommendations**| Based on extracted preferences, suggests cars with estimated price, features, safety rating, and unique selling points |
| **Built with LangChain**      | Implements structured output parsing for precision and clarity |
| **Simple Web UI (Streamlit)** | Minimalist UI for interaction and display of recommendations |

---

## Technical Stack

| Component        | Technology |
|------------------|------------|
| Frontend         | Streamlit |
| Backend Model    | LangChain + LLaMA 3.1 via Groq |
| Prompt Handling  | LangChain PromptTemplate |
| Data Extraction  | Pydantic Models for structured outputs |
| Configuration    | Python `dotenv` for API key management |

---

## Application Flow

1. **User Input**: Enters a natural language message indicating car preferences.
2. **Preference Extraction**: Uses a prompt to extract structured preferences (budget, type, features).
3. **Car Generation**: Feeds preferences into another prompt to generate a list of recommended cars.
4. **Display Output**: Recommendations are formatted and shown to the user in a `text_area`.

---

## Example Use Case

**Input**:  
"I’m looking for an electric hatchback under $25,000 with good mileage and advanced safety features."

**Output**:
```
🚗 Tesla Model 3 - $24,990
Key Features: Electric, Autopilot, Great Mileage
Safety Rating: 5-Star
Unique Feature: Full Self Driving Capability

Nissan Leaf - $23,500
Key Features: Electric, Compact, Eco Mode
Safety Rating: 5-Star
Unique Feature: Regenerative Braking

Chevrolet Bolt - $22,900
Key Features: Affordable, Long Range, Compact
Safety Rating: 4-Star
Unique Feature: Fast Charging
```

---

## Pydantic Models

```python
class UserPreferences(BaseModel):
    budget: str
    car_type: str
    features: List[str]

class CarRecommendation(BaseModel):
    name: str
    price: str
    features: List[str]
    safety_rating: str
    unique_feature: str

class CarRecommendations(BaseModel):
    recommendations: List[CarRecommendation]
```

---

## How to Run

1. Clone the repository.
2. Create a `key.env` file and add your GROQ API key:
   ```
   GROQ_API_KEY=your_api_key_here
   ```
3. Run:
   ```bash
   streamlit run app.py
   ```
4. Enter preferences and enjoy tailored car recommendations.

---

## License

This project is released under the MIT License.
