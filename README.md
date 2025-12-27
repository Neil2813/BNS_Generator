# BNS Generator: AI-Powered Legal Section Prediction

## Project Overview
The **BNS Generator** is a sophisticated AI application designed to assist legal professionals and researchers in identifying relevant sections of the **Bharatiya Nyaya Sanhita (BNS)** based on factual descriptions of criminal incidents. By leveraging advanced Natural Language Processing (NLP) and Graph Neural Networks (GNN), the system analyzes case facts and predicts the most applicable legal sections with high accuracy.

This project bridges the gap between raw textual facts and structured legal classification, streamlining the preliminary legal research process.

## Technology Stack

### Frontend (Client-Side)
- **Framework:** React 18 (via Vite)
- **Language:** TypeScript
- **Styling:** Tailwind CSS (Modern, utility-first styling) & Shadcn UI (Accessible components)
- **State Management:** React Hooks
- **HTTP Client:** Axios
- **Routing:** React Router DOM

### Backend (Server-Side & AI)
- **Framework:** FastAPI (High-performance Python web framework)
- **Language:** Python 3.9+
- **Machine Learning Libraries:** 
  - **PyTorch:** Core deep learning framework.
  - **Transformers (Hugging Face):** For Legal BERT implementation.
  - **Sentence Transformers:** For semantic search embeddings.
  - **FAISS:** Facebook AI Similarity Search for high-speed retrieval.
- **Graph Neural Networks:** Novel Heterogeneous Graph Attention Network (HGAT).

## System Architecture

The application follows a modern **Client-Server Architecture** decoupled via RESTful APIs.

1.  **Presentation Layer (Frontend):**
    - Accepts user input (case facts, victim details, etc.).
    - validating inputs and managing loading states.
    - Renders predictions and confidence scores in an interactive UI.

2.  **Application Layer (Backend API):**
    - Exposes endpoints (`/predict`, `/retrieve`) to the frontend.
    - Handles request validation and orchestrates the inference pipeline.
    - Integrates Prometheus for metric tracking.

3.  **Intelligence Layer (Model Pipeline):**
    - **Step 1: Encoding:** Input facts are encoded using **Legal BERT** to capture semantic meaning.
    - **Step 2: Retrieval (RAG):** A Retrieval-Augmented Generation module uses **FAISS** to find relevant BNS sections from a knowledge base.
    - **Step 3: Graph Processing (HGAT):** Retrieved sections and the input context are processed through a Heterogeneous Graph Attention Network to model relationships between different legal concepts.
    - **Step 4: Reranking:** A final scoring layer refines the predictions (using an optional XGBoost/sklearn reranker) to output the most probable sections.

## Workflow

1.  **Input:** The user navigates to the "Analyze" page and enters a narrative description of the crime (e.g., "A specific theft incident involving a weapon...").
2.  **Transmission:** The frontend sends a POST request to the backend with the facts and optional metadata (title, victim age, etc.).
3.  **Processing:**
    - The backend initializes the `RAGHGATWrapper`.
    - Facts are tokenized and embedded.
    - Similar existing legal sections are retrieved.
    - The graph model analyzes the connection between the facts and the legal code.
4.  **Output:** The backend returns a JSON response containing:
    - Predicted BNS Sections (ID, Name, Meaning).
    - Confidence Scores.
    - Evidence/Reasoning snippets.
5.  **Visualization:** The frontend displays the results as cards, highlighting "High Stakes" sections that may require human review.

---
*This documentation is designed to provide a high-level executive summary suitable for technical presentations and architectural reviews.*
