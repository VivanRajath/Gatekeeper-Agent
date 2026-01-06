# Gatekeeper Agent Verifier

This is my 5th agent. I created this agent to demonstrate a secure and verifiable AI interaction flow.

Live Demo: https://gatekeeper-agent-n7acqxl4zxfs4ryxjv89fm.streamlit.app/

## Architecture

This application is built using a modular architecture to ensure that AI-generated content is fact-checked before it is presented to the user.

1.  **User Interface (Streamlit)**: The front-end is built with Streamlit, providing a simple interface for users to enter queries or generate random "hallucinating" prompts to test the system.

2.  **Generation Layer (Groq)**: When a query is received, it is sent to Groq's API (using the Llama 3.3 model). This layer acts as the initial creative or informational generator, producing a raw response.

3.  **Verification Layer (Lyzr Gatekeeper)**: The raw response from Groq is not shown immediately. Instead, it is passed to the Lyzr Gatekeeper agent. This agent mimics a human reviewer with a specific set of strict instructions:
    *   It analyzes the content for factual accuracy.
    *   It checks for "hallucinations" (invented facts, fake movies, false dates).
    *   It rejects any content that claims fiction is reality.

4.  **Verdict Application**: The application receives the JSON decision from the Gatekeeper.
    *   **Approved**: The content is displayed to the user.
    *   **Rejected**: A rejection message is shown, along with the specific blocking issues cited by the Gatekeeper.

## Technology Stack

*   **Python**: Core programming language.
*   **Streamlit**: Web framework for the UI.
*   **Groq API**: For high-speed LLM generation.
*   **Lyzr AI**: For the autonomous Gatekeeper agent logic.
