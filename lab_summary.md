# Lab Summary

## Project goal

Build an advanced RAG system for legal-tech style retrieval over:

- the Trustworthy AI podcast transcript
- the EU AI Act PDF

The focus is on retrieval quality, metadata filtering, and reranking.

## What was implemented

### Step 1: Data preparation

- Loaded the podcast transcript and EU AI Act PDF.
- Attached metadata to each document:
  - `source_type`
  - `source_file`
  - `section`
- Compared chunking strategies before choosing a final configuration.
- Added a light cleanup pass for the PDF text to reduce OCR noise.
- Built `chunked_docs` with chunk-level metadata.

- Chunking outputs and reviews can be found in: `Chunking quality review_v1.md` and `Chunking quality review_v2.md` with corresponding comments.

### Step 2: Embeddings and baseline vectorstore

- Created embeddings with `text-embedding-3-small`.
- Built a Pinecone vectorstore from `chunked_docs`.
- Added a smoke test retrieval query to validate the index.

### Step 3: Metadata filtering

- Added filtered retrieval examples by:
  - `source_type`
  - `section`
- Compared unfiltered, podcast-only, and EU AI Act-only retrieval.

- The ouput is in the file: `Metadata filtering.md` 

- Also there is another file comparing between filtered and infiltered metadata: `Comparing filtered and unfiltered metadata.md` with corresponding comments.

### Step 4: RAG with reranking

- Added a reranking helper that scores retrieved candidates.
- Added answer synthesis from the reranked context.
- Built a compare cell for:
  - no reranking
  - reranking enabled
- Added debug output for the candidate pool before reranking.

### Step 5: Evaluation

- Added a manual evaluation section for the three-source comparison.
- Added a rerank vs no-rerank comparison block.
- Surface rerank scores and reasons for chosen chunks.

- Output and comments to be found in: `Performance evaluation with and without reranking.md`

## Key design choices

- The podcast transcript uses larger conversational chunks.
- The EU AI Act uses smaller chunks for precision.
- The PDF is lightly normalized before chunking.
- Reranking is limited to a small top set so the answer context stays focused.



