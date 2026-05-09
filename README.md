# Scoring and Rerankers

This repository contains a notebook-based lab for building and evaluating a retrieval pipeline over:

- the Trustworthy AI podcast transcript
- the EU AI Act PDF

The main working notebook is `Test_relevance_scoring_rerankers.ipynb`.

## How to run

1. Make sure your `.env` file contains the required API keys:
   - `OPENAI_API_KEY`
   - `PINECONE_API_KEY`

2. Open `Test_relevance_scoring_rerankers.ipynb` in Jupyter, VS Code, or another notebook runner.

3. Run the notebook from top to bottom.

4. If this is the first run in a fresh environment, execute the install cells near the top first so the required packages are available.

5. When prompted by the workflow, rerun the vectorstore cell after chunking so Pinecone is populated with the latest `chunked_docs`.

6. Inspect the comparison cells for:
   - chunking quality
   - metadata filtering
   - RAG with and without reranking
   - manual evaluation

## Repository map

### Root files

- `Lab.md`
  - Assignment brief and expected project steps.

- `README.md`
  - This guide.

- `lab_summary.md`
  - High-level summary of the implemented workflow and current state.

- `Test_relevance_scoring_rerankers.ipynb`
  - Main notebook used to build the solution step by step.

- `relevance_scoring_rerankers.ipynb`
  - Reference/original notebook in the repository.

- `Chunking quality review_v1.md`
  - Earlier notes on chunk quality.

- `Chunking quality review_v2.md`
  - Updated notes on chunk quality after cleanup and comparison.

- `Metadata filtering.md`
  - Notes about metadata filtering behavior.

- `Comparing filtered and unfiltered metadata.md`
  - Notes comparing filtered and unfiltered retrieval.

- `Performance evaluation with and without reranking.md`
  - Notes comparing retrieval with and without reranking.

- `.env`
  - Local environment variables for API keys.

- `.gitignore`
  - Git ignore rules for local files and artifacts.

### `Doc_sources/`

- `The_Blueprint_For_Trustworthy_AI.m4a`
  - Podcast audio source.

- `The_Blueprint_For_Trustworthy_AI.txt`
  - Transcript generated from the podcast audio.

- `eu_ai_act.pdf`
  - EU AI Act PDF source.

## What the notebook builds

- Loads the podcast transcript and EU AI Act PDF
- Adds metadata such as `source_type`, `source_file`, and `section`
- Compares chunking strategies before selecting a final chunk set
- Cleans the PDF text lightly before chunking
- Generates embeddings for all chunks
- Builds a Pinecone vectorstore
- Demonstrates metadata filtering
- Builds a RAG pipeline with reranking
- Compares retrieval quality with and without reranking
- Records a compact manual evaluation

## Notes

- The notebook is the authoritative implementation.
- If you rerun the vectorstore cell, the current `chunked_docs` set is what gets indexed.
- The source PDF text contains OCR artifacts, so the notebook includes a light cleanup pass before chunking.
