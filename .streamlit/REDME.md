🥗 MacroSnap

MacroSnap is an AI-powered nutrition buddy built with Streamlit,
Google Gemini, and Twilio WhatsApp.

Users enter their name and WhatsApp number once, then they can: - 💬 Ask
nutrition and food-related questions - 📸 Upload a meal photo for an AI
calorie and macro estimate - 🥩 Get estimated protein, carbohydrates,
and fat - 📝 Maintain a conversation with Gemini about their meals - 📲
Send a complete nutrition summary to their WhatsApp number

MacroSnap uses Gemini's chat and vision capabilities and does not
require OpenCV, MediaPipe, or custom model training.

✨ Features

🤖 AI Nutrition Chat

Chat with MacroSnap about food, meals, nutrition, and fitness-related
questions.

📸 Meal Image Analysis

Upload a .jpg, .jpeg, or .png image of a meal. Gemini analyzes the
image and provides an approximate: - Meal description - Calories -
Protein - Carbohydrates - Fat

Nutrition values are estimates and should not be treated as exact
measurements.

🧠 Conversation Memory

The Gemini chat session is maintained during the Streamlit session,
allowing follow-up questions such as asking about the protein in a meal
discussed earlier.

📲 WhatsApp Summary

After logging meals, users can click Send to WhatsApp. MacroSnap
asks Gemini to summarize the conversation and sends the summary through
Twilio's WhatsApp API.

🔐 Secure API Key Handling

API credentials are stored in Streamlit secrets instead of being
committed to GitHub.

🛠️ Tech Stack

Technology       Purpose

Python           Application logic
Streamlit        Web application and chat UI
Google Gemini    AI chat and meal image analysis
Twilio           WhatsApp messaging
google-genai   Gemini API client
twilio         Twilio Python SDK

📁 Project Structure

macrosnap/
├── app.py                         # Main Streamlit application
├── prompts.py                     # Gemini system and summary prompts
├── requirements.txt               # Python dependencies
├── .gitignore                     # Prevents secrets from being committed
└── .streamlit/
    └── secrets.toml.example       # Safe template for required secrets

.streamlit/secrets.toml is used locally but must never be
committed to GitHub.

⚙️ Requirements

Before running MacroSnap, install:

Python 3.9 or newer

A Google AI Studio account and Gemini API key

A Twilio account

Basic Python knowledge

🚀 Installation

1. Clone the repository

git clone https://github.com/Apoorva876/MacroFood.git
cd MacroFood

2. Create a virtual environment

Windows PowerShell

python -m venv venv
.\venv\Scripts\Activate.ps1

If PowerShell blocks activation:

Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass

Then activate again:

.\venv\Scripts\Activate.ps1

macOS / Linux

python3 -m venv venv
source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

🔑 API Configuration

MacroSnap requires credentials for Gemini and Twilio.

Gemini

Create a Gemini API key through Google AI Studio.

Twilio

Create a Twilio account and obtain:

Account SID

Auth Token

WhatsApp Sandbox number

WhatsApp Content Template SID

For the Twilio WhatsApp Sandbox, the testing phone number must join the
sandbox using the provided join code.

Create the local secrets file

Copy:

.streamlit/secrets.toml.example

to:

.streamlit/secrets.toml

Then add your real credentials:

GEMINI_API_KEY = "your-gemini-api-key"

TWILIO_ACCOUNT_SID = "your-twilio-account-sid"
TWILIO_AUTH_TOKEN = "your-twilio-auth-token"

TWILIO_WHATSAPP_FROM = "whatsapp:+14155238886"

TWILIO_CONTENT_SID = "your-content-template-sid"

⚠️ Important Security Rule

Never commit .streamlit/secrets.toml to GitHub.

Your .gitignore should contain:

.streamlit/secrets.toml

Only commit:

.streamlit/secrets.toml.example

If an API key has already been exposed publicly, revoke/rotate it before
continuing to use the project.

▶️ Run the Application

Start Streamlit with:

streamlit run app.py

The application normally opens at:

http://localhost:8501

🧑‍💻 How MacroSnap Works

1. User Onboarding

The user provides:

Name

WhatsApp number with country code

The information is stored in Streamlit session state for the current
session.

2. Gemini Chat Session

MacroSnap creates a Gemini chat session with a system prompt that
defines the AI as a nutrition buddy and keeps the conversation focused
on food, nutrition, meals, and fitness.

3. Text or Image Input

The chat interface accepts:

Text questions

Meal photos

Text + meal photo together

Meal images are passed to Gemini as image bytes using the Gemini SDK.

4. Nutrition Response

Gemini returns an approximate meal analysis containing the meal
description and estimated calories and macros.

5. Conversation Summary

When the user clicks Send to WhatsApp, MacroSnap asks Gemini to
summarize the meals discussed in the conversation and calculate a
running total.

6. WhatsApp Delivery

The generated summary is sent using Twilio's WhatsApp Content API and an
approved WhatsApp template.

💡 Example Use Case

A user can start by entering their details and then ask:

How many calories are in 2 eggs and 2 slices of toast?

They can then upload a meal photo and ask:

How much protein is approximately in this meal?

After logging their meals, they can select:

📤 Send to WhatsApp

MacroSnap generates a combined summary and sends it to their WhatsApp
number.

☁️ Deploy on Streamlit Community Cloud

Push the project to GitHub.

Open Streamlit Community Cloud.

Sign in with GitHub.

Create a new app.

Select the repository.

Select the main branch.

Set app.py as the entry point.

Open the app's Secrets settings.

Add the same values used in your local secrets.toml.

Deploy.

Do not upload or commit your local secrets.toml.

🔐 Privacy & Security

MacroSnap requires a user's WhatsApp number to send their nutrition
summary.

For production use, consider adding: - Clear privacy messaging - Secure
handling of personal information - Proper consent for WhatsApp
communication - Secure secret management - Rate limiting - Input
validation - Appropriate nutrition and medical disclaimers

⚠️ Disclaimer

MacroSnap provides AI-generated estimates of calories and
macronutrients. These estimates can vary because meal portions,
ingredients, preparation methods, and image quality may differ.

MacroSnap is intended for general informational purposes and is not a
substitute for professional medical, dietary, or nutritional advice.

📌 Project Status

MacroSnap is a Streamlit-based AI nutrition assistant using Gemini for
conversational and image-based meal analysis and Twilio for WhatsApp
summaries.

🙌 Acknowledgements

Built using:

Google Gemini

Streamlit

Twilio WhatsApp API