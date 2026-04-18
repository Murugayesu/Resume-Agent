# ResumeAgent

ResumeAgent is a Streamlit app that uses CrewAI to turn a resume, a job posting, a GitHub profile, and a short personal summary into two practical outputs:

1. A tailored resume focused on the target role.
2. Interview preparation material with likely questions and talking points.

This project was built as part of my learning journey with CrewAI. It helped me understand how to design a multi-agent workflow, pass context between tasks, and use specialized tools to produce a more structured result than a single prompt-driven app.

## What It Does

- Accepts a Markdown resume upload.
- Collects a job posting URL, GitHub profile URL, and personal write-up.
- Uses multiple CrewAI agents to research the role, profile the candidate, refine the resume, and prepare interview notes.
- Generates downloadable Markdown files for the tailored resume and interview materials.

## What I Learned From CrewAI

- How to split a complex goal into smaller agent roles with clear responsibilities.
- How task context can be shared between agents to build on earlier outputs.
- How tools such as web scraping, search, file reading, and semantic search improve agent quality.
- How to combine CrewAI with a local LLM through Ollama for a more controlled development setup.
- How to design an end-to-end workflow that feels like a product, not just a script.

## Tech Stack

- Python 3.12+
- Streamlit
- CrewAI
- CrewAI Tools
- Ollama with `llama3.1:8b`
- Serper search integration
- Hugging Face embeddings for semantic resume search

## How It Works

The application coordinates four agents:

- Tech Job Researcher: analyzes the job posting and extracts requirements.
- Personal Profiler: gathers and summarizes the candidate's background.
- Resume Strategist: tailors the resume to the target role.
- Engineering Interview Preparer: creates interview questions and talking points.

The workflow is designed so the later agents build on the research and profiling steps before generating the final outputs.

## Prerequisites

- Python 3.12 or newer
- Ollama installed and running locally
- A pulled Ollama model compatible with the app configuration, such as `llama3.1:8b`
- A Serper API key for web search

## Setup

1. Install dependencies:

	```bash
	uv sync
	```

2. Start Ollama locally and make sure the model is available.

3. Set your search API key in the environment:

	```bash
	set SERPER_API_KEY=your_key_here
	```

	On PowerShell, you can also use:

	```powershell
	$env:SERPER_API_KEY = "your_key_here"
	```

## Run the App

Start the Streamlit app with:

```bash
streamlit run main.py
```

Then provide:

- A Markdown resume file
- A job posting URL
- A GitHub profile URL
- A short personal summary

## Project Structure

- `main.py` - Streamlit UI and CrewAI workflow
- `pyproject.toml` - Project metadata and dependencies
- `README.md` - Project overview and setup instructions

## Notes

- The app writes temporary Markdown files during generation and removes them after use.
- Input resumes are expected in Markdown format for best results.
- The generated content should be reviewed before submitting it to employers.