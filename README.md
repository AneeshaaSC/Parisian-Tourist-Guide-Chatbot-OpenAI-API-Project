# 🇫🇷 Parisian Tourist Guide Chatbot: OpenAI API Project

This project creates a concise, AI-powered travel assistant for Paris, utilizing the OpenAI Chat Completions API. It's designed to simulate an interactive travel guide for Peterman Reality Tours by answering common tourist questions about key landmarks, art, and distances.

The core of the project is building a **`conversation`** history—a list of dictionaries—to manage the dialogue flow and instruct the model on its role as a Parisian expert.

## ✨ Project Title

`Parisian-Guide-Chatbot-OpenAI`

## 🎯 Project Goal

To use the OpenAI API to generate accurate, factual, and concise responses to a predefined set of Parisian tourist questions. The goal is to create a well-structured `conversation` list containing the system prompt, user questions, and the AI's generated answers, adhering to strict API parameters.

## 🛠️ Technology Stack

  * **Language:** Python
  * **API:** OpenAI Chat Completions API
  * **Library:** `openai`
  * **Model:** `gpt-3.5-turbo` (as used in the submitted notebook)

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

## 📝 Parisian Tourist Questions

The chatbot is specifically tasked with answering the following common tourist inquiries:

1.  How far away is the Louvre from the Eiffel Tower (in miles) if you are driving?
2.  Where is the Arc de Triomphe?
3.  What are the must-see artworks at the Louvre Museum?

## 🚀 How to Run the Code

### **Prerequisites**

1.  **Python:** Ensure you have Python installed.
2.  **Packages:** Install the necessary package:
    ```bash
    pip install openai
    ```
3.  **API Key:** This code **requires an OpenAI API Key**.

### **Setting up the API Key (Crucial Step)**

The line `client = OpenAI()` relies on finding your secret key in your environment variables for security. You **must** set the `OPENAI_API_KEY` environment variable before running the script.

  * **Linux/macOS (Temporary):**
    ```bash
    export OPENAI_API_KEY='your-secret-key-here'
    ```
  * **Windows (Temporary, Command Prompt):**
    ```bash
    set OPENAI_API_KEY=your-secret-key-here
    ```
    *It is recommended to set this as a permanent system variable.*

### **Execution**

1.  Save the Python code (from the notebook's logic) into a file (e.g., `paris_guide.py`).
2.  Run the script:
    ```bash
    python paris_guide.py
    ```

## 📈 Final `conversation` Output

After running the code, the `conversation` list contains the full dialogue history, including the initial example and the three question-and-answer pairs, structured as a list of dictionaries with alternating `'user'` and `'assistant'` roles.

```python
[
    {'role': 'system', 'content': 'You are a travel agent who provides useful information to tourists in Paris.'},
    {'role': 'user', 'content': 'What are the top 5 must-do things in Paris for tourists?'},
    {'role': 'assistant', 'content': '1. Eiffel Tower at sunset for skyline views. 2. Louvre Museum—book timed entry, focus on key sections. 3. Notre-Dame and nearby Sainte-Chapelle for Gothic architecture and stained glass. 4. Montmartre’s cobblestone lanes and Sacré-Cœur’s hilltop panorama. 5. Evening Seine River cruise to see landmarks illuminated. Bonus if time allows: Luxembourg Gardens stroll or a pastry stop in Le Marais.'},
    
    # --- Start of the Requested Questions ---
    
    {'role': 'user', 'content': 'How far away is the Louvre from the Eiffel Tower (in miles) if you are driving?'},
    {'role': 'assistant', 'content': 'The Louvre Museum is approximately 3 miles away from the Eiffel Tower if you are driving. The driving distance may vary depending on the route taken and traffic conditions.'},
    {'role': 'user', 'content': 'Where is the Arc de Triomphe?'},
    {'role': 'assistant', 'content': "The Arc de Triomphe is located at the western end of the Champs-Élysées avenue in Paris, France. It stands in the center of the Place Charles de Gaulle, also known as the Place de l'Étoile, from where 12 grand avenues radiate, including the famous Champs-Élysées."},
    {'role': 'user', 'content': 'What are the must-see artworks at the Louvre Museum?'},
    {'role': 'assistant', 'content': 'Some of the must-see artworks at the Louvre Museum include:\n1. Mona Lisa by Leonardo da Vinci\n2. Venus de Milo\n3. Winged Victory of Samothrace\n4. Liberty Leading the People by Eugène Delacroix\n5. The Wedding at Cana by Paolo Veronese\n6. The Raft of the Medusa by Théodore Géricault\n7. The Coronation of Napoleon by Jacques-Louis David\n8. Psyche Rev'} # Note: This response was cut short by max_tokens=100
]
```
