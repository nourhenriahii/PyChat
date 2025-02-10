<div style="border: 1px solid #ccc; padding: 20px; border-radius: 5px;">

# Chatbot GUI with OpenAI

This is a simple chatbot application built with Python using Tkinter for the graphical user interface (GUI) and the OpenAI API for natural language conversation. It allows users to interact with a chatbot directly through a desktop interface.

[![PyPI Version](https://img.shields.io/pypi/v/chatterbot)](https://pypi.org/project/chatterbot/)
[![Python Version](https://img.shields.io/badge/python-3.9-blue)](https://www.python.org/)
[![Django Version](https://img.shields.io/badge/django-2.0-green)](https://www.djangoproject.com/)
[![Maintainability](https://img.shields.io/badge/maintainability-high-brightgreen)](https://www.sonarqube.org/)


## Features

*   **GUI-based Chatbot:** Built using Tkinter for an interactive and user-friendly interface.
*   **Powered by OpenAI:** Uses the OpenAI GPT-3.5 Turbo model to provide dynamic and intelligent responses to user queries.
*   **Text-based Communication:** Send and receive messages through the GUI.

## Requirements

Before running the application, ensure you have the following:

*   Python 3.x
*   Tkinter (comes pre-installed with Python)
*   OpenAI Python library

## Installing Dependencies

To install the required dependencies, run the following command:

```bash
pip install openai
````

## Running Python Code with OpenAI and Tkinter

Here are the instructions to help you get started with the Python chatbot using OpenAI and Tkinter. You can open and run this code using a Python environment on your local machine, especially if you've installed the `openai` and `tkinter` libraries.

Follow these steps:

### 1\. Install the Requirements

Make sure Python is installed on your machine. Then, install the `openai` library if you haven't already:

```bash
pip install openai
```

### 2\. Install Tkinter

Tkinter comes pre-installed with Python on most systems. If not, install it by running:

```bash
pip install tk
```

### 3\. Create a New Python File

Open a text editor or IDE like Visual Studio Code or PyCharm, and create a new file (e.g., `chatbot.py`).

### 4\. Add Your Code

Copy and paste the chatbot code below into the `chatbot.py` file you just created.  **Remember to replace `"YOUR_API_KEY"` with your actual OpenAI API key.**

```python
import openai
import tkinter as tk
from tkinter import scrolledtext

openai.api_key = "YOUR_API_KEY"  # Replace with your actual API key

def send_message(message):
    try:
        response = openai.ChatCompletion.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a helpful assistant."},
                {"role": "user", "content": message}
            ]
        )
        return response.choices[0].message['content']
    except Exception as e:
        return f"Error: {e}"

def create_gui():
    window = tk.Tk()
    window.title("Chatbot")
    window.geometry("600x400")

    chat_display = scrolledtext.ScrolledText(window, wrap=tk.WORD, width=50, height=20)
    chat_display.pack(padx=10, pady=10)
    chat_display.insert(tk.END, "Welcome! How can I assist you today?\n\n")

    input_box = tk.Text(window, height=3, width=50)
    input_box.pack(padx=10, pady=5)

    def on_send():
        user_message = input_box.get("1.0", tk.END).strip()
        if user_message:
            chat_display.insert(tk.END, f"You: {user_message}\n")
            chat_display.see(tk.END)
            response = send_message(user_message)
            chat_display.insert(tk.END, f"Bot: {response}\n\n")
            chat_display.see(tk.END)
            input_box.delete("1.0", tk.END)

    send_button = tk.Button(window, text="Send", command=on_send)
    send_button.pack(pady=5)

    window.mainloop()

if __name__ == "__main__":
    create_gui()

```

### 5\. Run the Code

After saving the file, you can run it through the command prompt or terminal by executing:

```bash
python chatbot.py
```

### 6\. Launch the Chatbot GUI

A graphical user interface (GUI) window will appear where you can type messages and interact with the AI.

## Example Interaction

```
You: Hello!
Bot: Hi there! How can I help you today?
You: What is the weather like?
Bot: I do not have access to real-time information, such as weather.  You can check a weather app or website for current conditions.
```

## Contributing

Contributions are welcome\! Please open an issue or submit a pull request for any bug fixes, feature requests, or improvements.



