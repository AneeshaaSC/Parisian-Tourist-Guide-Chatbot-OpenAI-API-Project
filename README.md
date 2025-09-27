# 🇫🇷 Parisian Tourist Guide Chatbot: OpenAI API Project (Jupyter Notebook)

This README has been updated to reflect the project's use of a Jupyter Notebook and incorporates a "Further Steps" section based on our discussion for enhancing the chatbot's utility.

-----

## ✨ Project Title

`Parisian-Guide-Chatbot-OpenAI`

## 🎯 Project Goal

To use the OpenAI API to generate accurate, factual, and concise responses to a predefined set of Parisian tourist questions. The goal is to create a well-structured **`conversation`** history—a list of dictionaries—within a **Jupyter Notebook** to manage the dialogue flow and instruct the model on its role as a Parisian expert for Peterman Reality Tours.

## 🛠️ Technology Stack

  * **Development Environment:** Jupyter Notebook (`notebook.ipynb`)
  * **Language:** Python
  * **API:** OpenAI Chat Completions API
  * **Library:** `openai`
  * **Model:** `gpt-3.5-turbo` or equivalent (as used in the submitted notebook)

-----

## ⚙️ API Configuration

The project is configured to ensure deterministic and concise output, ideal for a fact-based guide:

| Parameter | Value | Purpose |
| :--- | :--- | :--- |
| **Model** | `gpt-3.5-turbo` | Used for faster, cost-effective, and highly capable general responses. |
| **`temperature`** | `0.0` | Eliminates randomness to ensure highly factual, repeatable, and non-creative answers. |
| **`max_tokens`** | `100` | Limits the response length to keep the guide's output concise and to the point. |

## 🧠 Model Behavior (System Prompt)

The conversation is initialized with a **`system`** role to set the model's behavior:

```python
"role": "system",
"content": "You are a travel agent who provides useful information to tourists in Paris."
```

-----

## 🚀 How to Run the Notebook

### **Prerequisites**

1.  **Python and Jupyter:** Ensure you have Python and a Jupyter environment (e.g., JupyterLab, VS Code with Python extension) installed.
2.  **Packages:** Install the necessary package:
    ```bash
    pip install openai
    ```
3.  **API Key:** This code **requires an OpenAI API Key**.

### **Setting up the API Key (Crucial Step)** 🔑

The line `client = OpenAI()` within the notebook relies on finding your secret key in your environment variables for security. You **must** set the `OPENAI_API_KEY` environment variable before running the relevant notebook cells.

  * **Linux/macOS (Temporary):**
    ```bash
    export OPENAI_API_KEY='your-secret-key-here'
    ```
  * **Windows (Command Prompt):**
    ```bash
    set OPENAI_API_KEY=your-secret-key-here
    ```

### **Execution**

1.  Open the `notebook.ipynb` file in your Jupyter environment.
2.  Ensure the API key is set in your environment.
3.  Run the cells sequentially to initialize the client, define the system prompt, send the questions, and print the final conversation log.

-----

## 💡 Further Steps to Make the Chatbot Useful

To transform this static Q\&A system into a dynamic, personalized trip planner, consider the following enhancements:

### **1. Dynamic Functionality (Tool Integration)** 🔗

Implement **Function Calling** or **RAG (Retrieval-Augmented Generation)** to connect the chatbot to real-time data sources:

| Enhancement | Tool/Integration Required | Value Added |
| :--- | :--- | :--- |
| **Real-Time Directions** | Google Maps or Routing API | Provide **live driving/metro times**, not just static distances. |
| **Current Conditions** | OpenWeatherMap API | Allow users to ask for the forecast and provide **weather-based activity suggestions** (e.g., move outside activities if rain is expected). |
| **Venue Availability** | Museum/Events APIs | Check **live opening hours** or ticket availability (e.g., "The Louvre is closed on Tuesdays."). |

### **2. Deep Personalization & Proactivity** 🧠

Modify the system prompt to make the AI a more proactive and personalized guide:

1.  **Initial Context Capture:** Force the chatbot to ask for the user's **travel dates, budget, and interests** (e.g., food, art, history) at the start of the conversation.
2.  **Itinerary Generation:** Shift the primary goal from answering questions to generating a **day-by-day itinerary** based on the captured preferences.
3.  **Refined Persona:** Enhance the system prompt to give the bot a specific, engaging personality (e.g., "Gaston, a witty Parisian local guide") to improve user engagement.
4.  **Constraint Management:** Increase the `max_tokens` (e.g., to `500+`) to allow for rich, descriptive itineraries and use the `seed` parameter for consistent persona and response style.

### **3. Improved Interactivity and Experience** 🗣️

1.  **Suggest Next Steps:** After answering a question, always offer a logical follow-up (e.g., "Since you asked about the Eiffel Tower, would you like me to suggest a nearby dinner spot?").
2.  **Multilingual Support:** Explicitly instruct the model to detect and respond in the user's input language (e.g., French, Spanish) to **widen accessibility**.
3.  **Error Handling:** Implement `try/except` blocks to manage API failures gracefully, falling back to a polite response instead of crashing.
