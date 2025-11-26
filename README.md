
# Local Web Researcher

A Python-based research assistant that uses locally hosted language models (via Ollama) to perform automated web research. It systematically investigates topics by breaking them down into focused areas, conducting searches, scraping content, and compiling findings with source citations.

## How It Works

The system takes a research question and executes a structured process:

1.  **Query Analysis:** The LLM analyzes your input and generates 5-7 specific, prioritized research areas.
2.  **Focused Investigation:** For each area, it:
    *   Creates targeted search queries
    *   Performs web searches
    *   Selects and scrapes relevant pages
    *   Extracts and saves content with source URLs
3.  **Iterative Research:** Based on initial findings, it can generate new research areas to explore deeper aspects of the topic.
4.  **Compilation:** All discovered content is saved to a timestamped text file.
5.  **Summary & Q&A:** When research concludes, the LLM provides a comprehensive summary and enters a conversation mode for follow-up questions about its findings.

## Setup

### Prerequisites

- Python 3.8+
- Ollama installed and running locally

### Installation

1.  **Clone and setup environment**
    ```bash
    git clone https://github.com/selenon/local-web-researcher.git
    cd local-web-researcher
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

2.  **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Configure the model**
    Edit `llm_config.py` to specify your Ollama model:
    ```python
    LLM_CONFIG_OLLAMA = {
        "model_name": "phi3:14b-medium-128k-instruct",  # Your model name
        "n_ctx": 55000,  # Context size
        "temperature": 0.7,
        # ... other settings
    }
    ```

### Recommended Models

- `phi3:3.8b-mini-128k-instruct`
- `phi3:14b-medium-128k-instruct`

## Usage

1.  **Start Ollama service**
    ```bash
    ollama serve
    ```

2.  **Run the researcher**
    ```bash
    python Web-LLM.py
    ```

3.  **Start research session**
    - Type `@` followed by your research question
    - Press `CTRL+D` to submit
    - Example: `@What are the current limitations of solid-state batteries?`

### Research Controls

During operation, use these commands (submit with `CTRL+D`):

- `s` - Show current research status
- `f` - Display active focus areas
- `p` - Pause for progress assessment
- `q` - Quit research and generate summary

## Output

The system creates a detailed research file containing:
- All extracted content with source URLs
- Research focus areas investigated
- Final summary and analysis
- Timestamp of the session

## Configuration

Modify `llm_config.py` to adjust:
- Model parameters (temperature, context size)
- Search and scraping behavior
- Output formatting

## Current Status

Functional prototype. Tested with Phi-3 models and performs structured research tasks effectively. The iterative research approach often uncovers unexpected but relevant aspects of complex topics.

## Notes

- This is my second programming project - feedback and contributions are welcome
- The system respects website terms of service and robots.txt
- All processing happens locally via your Ollama instance
- Research quality depends on the underlying model's capabilities

## License

MIT
