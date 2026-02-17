# LangGraph Community Investment Group Leadership Agent

This repository contains a LangGraph implementation for a role-based leadership routing system that directs user queries to the appropriate organizational leader based on their domain expertise.

## Overview

The system consists of a workflow that:
1. Receives user queries
2. Classifies which leader should handle the query
3. Routes the query to the appropriate leader
4. Generates a response from the leader based on their role and expertise

## Prerequisites

- Python 3.13+
- Google Gemini API key

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Stevealila/LangGraph-Community-Investment-Group-Leadership-Agent.git
cd LangGraph-Community-Investment-Group-Leadership-Agent
```

2. Set up a virtual environment and install dependencies:
```bash
# Using uv (recommended) — creates venv and installs dependencies in one step
pip install uv
uv sync

# OR using pip
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

4. Set up environment variables:
```bash
# Copy the example .env file
cp .env.example .env

# Edit the .env file with your actual Google API key
# GOOGLE_API_KEY=your_api_key_here
```

## Usage

### Running the Agent

You can use the leadership agent in your Python code:

```python
from agent import graph

# Initialize with a user query
result = graph.invoke({
    "user_query": "When is our next meeting scheduled?"
})

# Access the response from the appropriate leader
print(result["leader_response"])
```

### Example Queries

Try these example queries to test different leader responses:

- Chairman: "What's our strategic direction for this quarter?"
- Secretary: "Can you share the minutes from last month's meeting?"
- Treasurer: "I need to request a refund for an event payment."
- ICT: "The login page on our website isn't working correctly."

## Project Structure

- `agent.ipynb` - Main implementation of the LangGraph workflow
- `requirements.txt` - Dependencies required for the project
- `.env.example` - Template for environment variables

## How It Works

1. **State Management**: The workflow keeps track of the user query, assigned leader, and leader's response.

2. **Classification**: The system analyzes the query to determine which leader should handle it based on their domains of expertise:
   - Chairman: Oversight, meetings, executive decisions
   - Secretary: Minutes, documentation, records
   - Treasurer: Payments, refunds, financial matters
   - ICT: Web application, technical support, maintenance

3. **Routing**: The query is directed to the appropriate leader based on the classification.

4. **Response Generation**: The system generates a response from the assigned leader, mimicking their communication style and expertise.

## Customization

You can customize the system by:

1. **Modifying Leader Roles**: Edit the `ClassifierSchema` and prompt templates to adjust roles and responsibilities
2. **Adjusting Communication Styles**: Update the prompt templates in each leader's response function
3. **Adding New Leaders**: Extend the `ClassifierSchema` and add new leader response functions

## Troubleshooting

- **API Key Issues**: Ensure your Google API key is correctly set in the `.env` file
- **Classification Errors**: If queries are being routed incorrectly, adjust the prompt in the classifier function
- **Import Errors**: Make sure all dependencies are installed via `requirements.txt`

## Dependencies

- langchain - Core framework for LLM operations
- langchain-google-genai - Integration with Google's Gemini models
- langgraph - Graph-based workflows for LLM applications
- pydantic - Data validation and settings management

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
