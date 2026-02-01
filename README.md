# פרטי מגישים

- גאנא ו– 325407864  
- היא ג – 207747486  
- ג׳ומאנה ק – 208169912  
- ג׳ואנה ע – 212387575

README – Experimental RAG System Implementation
Project Overview
This project presents an experimental implementation of a Retrieval-Augmented Generation (RAG) system, developed as part of a course assignment and based on the concepts introduced in the course lectures.
The objective of the assignment is to experimentally explore different components of a RAG pipeline and analyze how design choices affect retrieval quality and answer generation.
Specifically, the project examines:
•	Different chunking strategies
•	Different retrieval / indexing algorithms
•	A comparison between a local LLM and an external LLM API
The system is implemented in Python using a Jupyter Notebook and follows a modular, experimental approach.
 
Document Collection and Text Extraction
The knowledge base of the system consists of several PDF documents provided as part of the assignment.
Since RAG systems operate on text rather than raw documents, all PDF files are first converted into plain text using PyMuPDF.
During the extraction process, each text segment is enriched with metadata to preserve traceability:
•	The original PDF file name
•	The page number from which the text was extracted
This metadata enables transparent tracking of which document sections contributed to each generated answer.
 
Chunking Strategy
After text extraction, the documents are split into smaller textual units using a chunking mechanism.
Chunking is a critical stage in RAG systems, as it directly influences retrieval precision and contextual coherence.
Two chunking strategies are implemented and compared:
•	No-overlap chunking
•	Overlapping chunking
Each chunk is generated with a fixed size, and in the overlapping configuration a partial overlap is applied between consecutive chunks.
This overlap helps maintain continuity between adjacent text segments and reduces the risk of losing important contextual information at chunk boundaries.
The chunking strategy is applied consistently across documents to allow a fair comparison between retrieval and generation approaches.
 
Retrieval Methods and Experimental Comparison
To explore different retrieval techniques, the system implements and compares two retrieval methods.
TF-IDF Retrieval
The first retrieval method is based on TF-IDF vectorization combined with cosine similarity.
This approach captures lexical similarity and is effective when the user query shares explicit keywords with the source text.
Embedding-Based Retrieval
The second retrieval method uses semantic embeddings generated with the
all-MiniLM-L6-v2 Sentence-Transformers model.
By comparing dense vector representations rather than keywords, this method is capable of retrieving text chunks that are semantically relevant even when the wording differs significantly from the query.
In practice, embedding-based retrieval generally produced more contextually meaningful results, while TF-IDF remained effective for keyword-oriented queries.
 
Large Language Models (LLMs)
As part of the experimental requirements, the system was designed to compare different LLM configurations.
Local LLM
A local LLM setup was implemented using Ollama, avoiding dependency on external APIs.
This configuration allows full local execution and greater control over the generation process.
External LLM API
In addition, an external LLM was integrated using the Google Gemini API.
This enabled a direct comparison between locally hosted models and cloud-based LLMs, using the same retrieved context.
The comparison highlights differences in response quality, verbosity, and adherence to the provided context.
 
RAG Answer Generation
For each user query, the system performs the following steps:
1.	Retrieve the most relevant chunks using either TF-IDF or embedding-based retrieval
2.	Construct a context block from the retrieved chunks, limited by a predefined maximum length
3.	Send the query and retrieved context to the selected LLM (local or external)
4.	Generate a concise answer based strictly on the provided context
For transparency and analysis purposes, the system also reports:
•	The retrieved chunk identifiers
•	Similarity scores produced during retrieval
 
Experimental Findings
The experimental results emphasize the importance of component selection in RAG systems.
•	Embedding-based retrieval demonstrated greater robustness for semantic queries.
•	TF-IDF retrieval remained useful for keyword-focused questions.
•	Overlapping chunking generally improved contextual continuity.
•	Both local and external LLMs were capable of supporting RAG pipelines, though external models often produced more fluent responses, while local models offered greater controllability and independence from APIs.
 
Submission Contents
The submission includes:
•	A Jupyter Notebook containing the full implementation and experimental runs
•	The PDF documents used as the knowledge base
•	This README file describing the system design and findings
•	A short demonstration video (5–6 minutes)
 
Conclusion
This project demonstrates a complete and experimental RAG pipeline, from document ingestion and preprocessing to retrieval and answer generation.
By systematically comparing chunking strategies, retrieval algorithms, and LLM configurations, the project fulfills the experimental objectives of the assignment and provides practical insights into the design trade-offs involved in Retrieval-Augmented Generation systems.
 
Bonus
As part of the project, additional experimental comparisons were conducted to deepen understanding of RAG system behavior.
Specifically, TF-IDF-based retrieval was compared with semantic embedding-based retrieval (Sentence-Transformers), analyzing the retrieved chunks, similarity scores, and their relevance to the user query.
In addition, a comparison was performed between different LLM configurations, including a local LLM (LLaMA via Ollama) and an external LLM (Gemini API), using identical queries and retrieved contexts.
These experiments enabled an evaluation of differences in answer quality, level of detail, and adherence to retrieved information.
This experimental exploration demonstrates a practical understanding of how algorithmic and model choices impact RAG system performance and constitutes the bonus component of the assignment.
 
Data
The PDF files used in this project are stored in Google Drive.
Drive link:
https://drive.google.com/drive/folders/1wTqfUmAx7O9j62vo8ahDA4ySjAWYkO9C?usp=sharing

