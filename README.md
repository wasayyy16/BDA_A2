# BDA_A2
Fundamentals of Big Data Analytics : Assignment 2
Report : 
Building a Basic Search Engine with MapReduce

Introduction

In this project, we aim to develop a basic search engine using the MapReduce framework. The goal is to index a collection of documents and process user queries to retrieve relevant documents. The project leverages the MRJob library, which provides a convenient interface for writing MapReduce jobs in Python.

Overview of the Code

The code consists of two main classes: Indexer and Query. The Indexer class is responsible for indexing the documents, while the Query class handles user queries.

Indexing Documents

The Indexer class defines a MapReduce job with two main steps: tokenization and index creation. In the mapper_tokenize method, each document is tokenized to extract words from the SECTION_TEXT field. The tokens are then emitted as key-value pairs, where the word serves as the key and the ARTICLE_ID serves as the value.

The reducer_create_index method receives the word-document pairs and creates an inverted index. It removes duplicate document IDs and yields the final inverted index for each word.

Processing Queries

The Query class defines a MapReduce job to process user queries. The mapper_tokenize_query method tokenizes the query text and emits word-query pairs. The reducer_rank_documents method receives the word-query pairs and ranks relevant documents based on the inverted index created by the Indexer class. The relevant documents are sorted based on their relevance to the query and emitted as output.

Command-Line Interface

The code includes a command-line interface (CLI) to specify the type of job (index or query), the input file path, and the query text (for query jobs). It uses the argparse library to parse command-line arguments and initialize the appropriate MRJob class based on the job type.

Execution

To run the code, you can use the following command:



python3 search_engine.py query input_file.txt --query "your query text"



Conclusion

In conclusion, the provided code demonstrates the use of MapReduce to build a basic search engine. It showcases the power of the MapReduce paradigm in processing large datasets efficiently and provides a foundation for building more complex search engines in the future.
