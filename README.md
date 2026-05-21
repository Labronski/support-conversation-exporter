# Support Conversation Exporter

A lightweight Flask web application that queries the Intercom API to pull support conversation data by date range and exports it to CSV for analysis.

Built as a hackathon project to streamline support data workflows and reduce the manual effort required to extract and analyze conversation trends.

---

## What It Does

Support teams deal with large volumes of conversations that are difficult to analyze in bulk through standard tooling. This tool provides a simple browser-based UI where you can select a date range, run a script, and get a clean CSV export of conversations — including summaries, full transcripts, and issue category attributes — ready for analysis or reporting.

---

## Features

- Simple web UI for selecting date ranges and running exports
- Intercom API integration with full pagination support for large result sets
- Filters conversations by product area using custom conversation attributes
- Exports to CSV with conversation ID, AI-generated summary, transcript, and issue category
- Handles HTML tag stripping and UTF-8 encoding for clean output
- Modular script structure — easy to add new product area filters

---

## Tech Stack

- **Python** / **Flask** — web framework and script runner
- **Intercom REST API** — conversation data source
- **CSV** — export format

---

## Project Structure

```
├── app.py              # Flask app — serves the UI and triggers script execution
├── scripts/
│   ├── script1.py      # Exports conversations filtered by product area (e.g. Ramps)
│   └── wallet.py       # Exports wallet-related conversations with transcripts
└── templates/
    └── index.html      # Web UI with date range inputs
```

---

## Setup

### Prerequisites

- Python 3.8+
- Intercom API access token with read permissions on conversations

### Installation

```bash
# Clone the repo
git clone https://github.com/Labronski/support-conversation-exporter.git
cd support-conversation-exporter

# Install dependencies
pip install flask requests python-dotenv

# Set up environment variables
cp .env.example .env
# Add your INTERCOM_ACCESS_TOKEN to .env
```

### Running

```bash
python app.py
```

Open `http://localhost:5000` in your browser, enter a date range, and run an export.

---

## Configuration

Set the following in your `.env` file:

```
INTERCOM_ACCESS_TOKEN=your_token_here
```

To export different product areas, duplicate one of the scripts in `/scripts` and update the `filter_conversations_by_product()` call with your target area name.

---

## Example Output

The CSV export includes:

| conversation_id | summary | transcript | issue_category |
|----------------|---------|------------|----------------|
| 12345 | User unable to complete transaction... | user: My swap failed... | Transaction Failed |

---

## Notes

This project requires Intercom API credentials. The `.env` file is excluded from version control — never commit your API token directly in source code.
