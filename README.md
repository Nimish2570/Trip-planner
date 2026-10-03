# ✈️ TripPlanner

**Plan your next trip without opening a dozen browser tabs.**

TripPlanner is a multi-agent AI travel planner that turns a simple travel request into a complete trip plan.

Just tell it what you're looking for in plain English:

> *"Plan a 10-day Europe trip from India in April with a mid-range budget."*

TripPlanner researches the trip for you and brings everything together — flights, hotels, weather, budget estimates, and a practical day-by-day itinerary.

The goal is simple: **spend less time researching your trip and more time looking forward to it.**

---

## 🌍 What can TripPlanner do?

Travel planning usually means jumping between flight websites, hotel sites, weather apps, maps, blogs, and a notes app.

TripPlanner brings those pieces together using multiple AI agents, with each agent focusing on a different part of the trip.

|                   | What it does                                                                           |
| ----------------- | -------------------------------------------------------------------------------------- |
| ✈️ **Flights**    | Finds relevant airports, airlines, typical flight durations, and estimated fare ranges |
| 🏨 **Hotels**     | Researches accommodation options based on your destination and budget                  |
| 🌤️ **Weather**   | Checks current conditions and forecasts and provides useful travel context             |
| 🗺️ **Itinerary** | Creates a realistic day-by-day plan based on your trip                                 |
| 💰 **Budget**     | Provides an estimated breakdown of the overall trip cost                               |

Once the research is complete, the different pieces are combined into one travel plan that you can actually use.

Your trips are also saved, so you can come back later and continue the conversation without starting from scratch.

---

## ✨ Features

* 💬 Describe your trip naturally instead of filling out complicated forms
* 🤖 Multiple AI agents working on different parts of your trip
* ✈️ Flight research
* 🏨 Hotel research
* 🌤️ Weather information
* 🗺️ Day-by-day itineraries
* 💰 Estimated trip budgets
* 💾 Automatically saved trips
* 🔄 Continue conversations about an existing trip
* 📝 Trip builder for users who prefer forms
* 📥 Export plans as Markdown
* 🖨️ Print your travel plans
* 🌙 Light and dark mode

---

# 🚀 Getting Started

Want to run TripPlanner locally? Here's everything you need.

## Prerequisites

Before getting started, make sure you have:

* **Python 3.11**
* **[uv](https://docs.astral.sh/uv/)** for managing Python dependencies
* A **PostgreSQL database**
* API keys for the services TripPlanner uses

You can use a free PostgreSQL instance from [Render](https://render.com/) if you don't already have a database.

### API keys

You'll need API keys from:

* [Groq](https://console.groq.com/)
* [Tavily](https://tavily.com/)
* [AviationStack](https://aviationstack.com/)
* [OpenWeather](https://openweathermap.org/api)

---

## 📦 Installation

### 1. Clone the repository

```bash
git clone https://github.com/Nimish2570/Trip-planner.git
cd TripPlanner-Multi-Agent-AI-Travel-Planner
```

### 2. Install dependencies

TripPlanner uses `uv` to manage its Python environment and dependencies.

```bash
uv sync
```

If you don't have `uv` installed yet, follow the official installation instructions:

https://docs.astral.sh/uv/getting-started/installation/

---

## 🔐 Configure environment variables

Create a `.env` file in the root of the project:

```dotenv
# Required
GROQ_API_KEY=your_groq_key
DATABASE_URL=postgresql://user:password@host:5432/dbname

# Travel data providers
TAVILY_API_KEY=your_tavily_key
AVIATIONSTACK_API_KEY=your_aviationstack_key
OPENWEATHER_API_KEY=your_openweather_key

# Optional
GROQ_MODEL=openai/gpt-oss-20b
```

### What do these variables do?

| Variable                | Required | Purpose                                            |
| ----------------------- | :------: | -------------------------------------------------- |
| `GROQ_API_KEY`          |     ✅    | Used for AI-powered trip planning                  |
| `DATABASE_URL`          |     ✅    | Stores your trips and conversation data            |
| `TAVILY_API_KEY`        |     ✅    | Used for web research, including hotel information |
| `AVIATIONSTACK_API_KEY` |     ✅    | Provides airport and airline information           |
| `OPENWEATHER_API_KEY`   |     ✅    | Provides weather and forecast information          |
| `GROQ_MODEL`            |     ❌    | Lets you choose which Groq model to use            |

> ⚠️ **Never commit your `.env` file or expose your API keys.**

---

## ▶️ Run the application

Once everything is configured, start the app with:

```bash
uv run python app.py
```

Then open:

**http://127.0.0.1:8000**

If the application loads and you see the **API connected** indicator in the sidebar, you're ready to plan your first trip.

---

# 🧳 Using TripPlanner

## 💬 Plan a trip with natural language

You don't need to learn a special format.

Just describe the trip the way you would describe it to another person.

For example:

> **"Plan a 10-day Europe trip from India in April with a mid-range budget."**

Or:

> **"I want a relaxed 5-day trip to Rome and Florence in September for two people."**

TripPlanner will interpret your request and start researching the different parts of your trip.

Depending on the request and the services being used, generating a complete plan can take around **30–90 seconds**.

You'll see the different stages as the plan is being created.

---

## 🛠️ Use the trip builder

If you prefer filling out a form instead of writing a prompt, TripPlanner has a trip builder too.

Click the **sliders icon** next to the message box.

You can enter things like:

* Origin
* Destination
* Travel dates
* Trip duration
* Number of travellers
* Budget
* Interests and preferences

Once you're finished, click **Write my prompt**.

TripPlanner will turn those details into a natural-language request that you can review, edit, and send.

---

## 📋 Explore your travel plan

Once your plan is ready, the results are organized into separate sections:

* **Plan** — your overall trip summary
* **Itinerary** — your day-by-day schedule
* **Flights** — flight and airport information
* **Hotels** — accommodation research
* **Weather** — weather information and travel considerations

This makes it easier to jump directly to the information you're looking for.

---

## 💾 Save, revisit, and export

Your trips are automatically saved in the sidebar.

You can:

* Open an old trip and continue the conversation
* Ask follow-up questions
* Copy your plan
* Download it as Markdown
* Print your plan
* Start a completely new trip
* Switch between light and dark mode

So your travel research doesn't disappear when you close the browser.

---

# 🐛 Troubleshooting

## The application loads, but planning doesn't work

First, check the API status indicator at the bottom of the sidebar.

If it says **API unreachable**, the backend may have stopped.

Restart the application:

```bash
uv run python app.py
```

If the problem continues, check the terminal where you started the application. It should contain the underlying error.

---

## The model doesn't exist

AI models can be retired, renamed, or replaced over time.

If Groq reports that your configured model doesn't exist, you can check the models available to your API key.

Using PowerShell:

```powershell
curl https://api.groq.com/openai/v1/models `
  -H "Authorization: Bearer $env:GROQ_API_KEY"
```

Using macOS/Linux:

```bash
curl -s https://api.groq.com/openai/v1/models \
  -H "Authorization: Bearer $GROQ_API_KEY"
```

Choose an available model and update your `.env` file:

```dotenv
GROQ_MODEL=your_model_name
```

Then restart TripPlanner.

---

## `DATABASE_URL` is missing

TripPlanner uses PostgreSQL to save trips.

Make sure your `.env` file contains a valid database connection string:

```dotenv
DATABASE_URL=postgresql://user:password@host:5432/dbname
```

If you're using a hosted PostgreSQL provider, copy the connection string provided by that service.

---

## Plans are taking a while to generate

That's expected.

TripPlanner isn't simply generating an answer from an LLM. Multiple agents research different parts of your trip, and those agents may make external API and web requests.

A complete plan can therefore take around **30–90 seconds**.

---

# 🤝 Contributing

Contributions are welcome!

If you have an idea for a new feature, find a bug, or want to improve something, feel free to open an issue or submit a pull request.

## Getting started

1. Fork the repository.
2. Clone your fork.
3. Follow the [Getting Started](#-getting-started) instructions.
4. Create a branch for your change:

```bash
git checkout -b feature/your-feature-name
```

## Making changes

A few things to keep in mind:

* Keep pull requests focused on one change.
* Follow the existing coding style.
* Test the application before submitting your PR.
* Don't commit `.env` files or API keys.
* Keep documentation updated when you change user-facing functionality.

## Commit your changes

For example:

```bash
git add .
git commit -m "Add support for multi-city trips"
```

Then push your branch:

```bash
git push origin feature/your-feature-name
```

Open a pull request against the `main` branch and explain:

* What you changed
* Why you changed it
* How you tested it

---

## 🐞 Found a bug?

Open an issue on the project's GitHub repository:

https://github.com/Nimish2570/Trip-planner/issues

When reporting a bug, it helps to include:

* What you were trying to do
* What you expected to happen
* What actually happened
* Any error messages
* Relevant terminal output

The more context you provide, the easier it is to reproduce and fix the problem.

---

# 🙌 Acknowledgements

TripPlanner wouldn't be possible without the services it builds on.

* [Groq](https://groq.com/) — AI inference
* [Tavily](https://tavily.com/) — web research
* [AviationStack](https://aviationstack.com/) — aviation and airport information
* [OpenWeather](https://openweathermap.org/) — weather data

A big thank you to the teams behind these services for making their APIs available to developers.

---

# 📄 License

TripPlanner is licensed under the **GNU General Public License v3.0**.

See the [LICENSE](LICENSE) file for the full license text.

---

<p align="center">
  Made with ❤️ for people who'd rather travel than spend hours planning.
</p>
