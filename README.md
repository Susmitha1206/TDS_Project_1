# DataWorks Automation Agent

This project implements an automation agent for DataWorks Solutions, designed to process various data artifacts and perform routine tasks. The agent leverages a Large Language Model (LLM) to interpret plain-English task descriptions and execute the necessary steps, ensuring verifiable and consistent outputs.  It adheres to strict security and operational guidelines, including data containment within designated directories and prevention of data deletion.

## Features

* **Task Execution:** Accepts plain-English task descriptions via a REST API endpoint (`/run?task=<task description>`).
* **LLM Integration:** Utilizes an LLM (GPT-4o-Mini via AI Proxy) to parse task instructions and orchestrate multi-step processes.
* **Output Verification:** Provides a read endpoint (`/read?path=<file path>`) to retrieve the content of generated files for verification against expected results.
* **Data Security:** Enforces strict data containment within the `/data` directory and prevents data deletion, adhering to DataWorks security policies.
* **Automated Operations:** Handles a range of operational tasks, including data generation, formatting, analysis, and extraction.  (See "Implemented Tasks" section for details)
* **Business Task Support:** Extends functionality to encompass broader business tasks like API interaction, Git operations, database queries, web scraping, image manipulation, audio transcription, and document conversion. (See "Implemented Tasks" section for details)
* **Extensible Design:**  Designed to accommodate future task additions and evolving business needs.
* **Dockerized Deployment:**  Packaged as a Docker image for easy deployment and portability.

## Implemented Tasks

This agent implements the following tasks, categorized by DataWorks teams:

**Phase A: Operations Tasks**

* **A1:** Install `uv` (if necessary) and execute `datagen.py` to generate data files.
* **A2:** Format Markdown files using `prettier`.
* **A3:** Count Wednesdays in a list of dates.
* **A4:** Sort contacts in a JSON file.
* **A5:** Extract the first line of the 10 most recent log files.
* **A6:** Create an index of H1 headings in Markdown files.
* **A7:** Extract the sender's email address from an email message using LLM.
* **A8:** Extract a credit card number from an image using LLM.
* **A9:** Find the most similar pair of comments using embeddings.
* **A10:** Calculate total sales for "Gold" ticket type from a SQLite database.

**Phase B: Business Tasks**

* **B3:** Fetch data from an API and save it.
* **B4:** Clone a Git repository and make a commit.
* **B5:** Run a SQL query on a SQLite or DuckDB database.
* **B6:** Extract data (scrape) from a website.
* **B7:** Compress or resize an image.
* **B8:** Transcribe audio from an MP3 file.
* **B9:** Convert Markdown to HTML.
* **B10:** Create an API endpoint to filter a CSV file and return JSON data.

## Getting Started

1. **Clone the repository:** `git clone https://github.com/your-username/repo-name.git`
2. **Set AI Proxy Token:** Export your AI Proxy token as an environment variable: `export AIPROXY_TOKEN="your_token"`
3. **Build the Docker image:** `docker build -t your-username/repo-name .`
4. **Run the Docker container:** `docker run -p 8000:8000 -e AIPROXY_TOKEN=$AIPROXY_TOKEN your-username/repo-name`

The API will be accessible at `http://localhost:8000`.

## Usage

* **Run a task:** `POST http://localhost:8000/run?task=<task description>`
* **Read a file:** `GET http://localhost:8000/read?path=<file path>`

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## License

MIT License. See the `LICENSE` file for details.
