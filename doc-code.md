# Documentation Augmented Code Generation

## Without documentation

<details>
<summary>PROMPT</summary>

write a python program with LlamaIndex interface to implement semantic search on the documents at https://gpt-index.readthedocs.io/en/latest/index.html

</details>

[GPT-4 “hallucinates”](//ai-llm.github.io/doc-code/semantic-search-with-llamaindex.html) on [LlamaIndex](https://gpt-index.readthedocs.io/en/latest/index.html) which started from 2022 after the models were trained.

## With documentation

<details>
<summary>PROMPT</summary>

Build and Query Index
Create a new .py file with the following:
```python
from llama_index import GPTSimpleVectorIndex, SimpleDirectoryReader

documents = SimpleDirectoryReader('data').load_data()
index = GPTSimpleVectorIndex.from_documents(documents)
```

This builds an index over the documents in the data folder (which in this case just consists of the essay text). We then run the following
```python
response = index.query("What did the author do growing up?")
print(response)
```

You should get back a response similar to the following: The author wrote short stories and tried to program on an IBM 1401.

===

According to above LlamaIndex documentation，write a python program with LlamaIndex interface to implement semantic search on the documents at https://gpt-index.readthedocs.io/en/latest/index.html
</details>

Both [GPT-3.5](//ai-llm.github.io/doc-code/doc-code-llamaindex-3-5.html) and [GPT-4](//ai-llm.github.io/doc-code/doc-code-llamaindex-4.html) learn.

## With more documentation

<details>
	<summary>PROMPT</summary>

Build and Query Index
Create a new .py file with the following:
```python
from llama_index import GPTSimpleVectorIndex, SimpleDirectoryReader

documents = SimpleDirectoryReader('data').load_data()
index = GPTSimpleVectorIndex.from_documents(documents)
```

This builds an index over the documents in the data folder (which in this case just consists of the essay text). We then run the following
```python
response = index.query("What did the author do growing up?")
print(response)
```
You should get back a response similar to the following: The author wrote short stories and tried to program on an IBM 1401.

===
Data Connectors (LlamaHub 🦙)
Our data connectors are offered through LlamaHub 🦙. LlamaHub is an open-source repository containing data loaders that you can easily plug and play into any LlamaIndex application.

Some sample data connectors:
local file directory (SimpleDirectoryReader). Can support parsing a wide range of file types: .pdf, .jpg, .png, .docx, etc.
Notion (NotionPageReader)
Google Docs (GoogleDocsReader)
Slack (SlackReader)
Discord (DiscordReader)

===
LlamaIndex Usage Pattern
The general usage pattern of LlamaIndex is as follows:
Load in documents (either manually, or through a data loader)
Parse the Documents into Nodes
Construct Index (from Nodes or Documents)
[Optional, Advanced] Building indices on top of other indices
Query the index
1. Load in Documents
The first step is to load in data. This data is represented in the form of Document objects. We provide a variety of data loaders which will load in Documents through the load_data function, e.g.:

```python
from llama_index import SimpleDirectoryReader

documents = SimpleDirectoryReader('data').load_data()
```

You can also choose to construct documents manually. LlamaIndex exposes the Document struct.

```python
from llama_index import Document

text_list = [text1, text2, ...]
documents = [Document(t) for t in text_list]
```

A Document represents a lightweight container around the data source. You can now choose to proceed with one of the following steps:
Feed the Document object directly into the index (see section 3).
First convert the Document into Node objects (see section 2).
2. Parse the Documents into Nodes
The next step is to parse these Document objects into Node objects. Nodes represent “chunks” of source Documents, whether that is a text chunk, an image, or more. They also contain metadata and relationship information with other nodes and index structures.
Nodes are a first-class citizen in LlamaIndex. You can choose to define Nodes and all its attributes directly. You may also choose to “parse” source Documents into Nodes through our NodeParser classes.
For instance, you can do

```python
from llama_index.node_parser import SimpleNodeParser

parser = SimpleNodeParser()

nodes = parser.get_nodes_from_documents(documents)
```

You can also choose to construct Node objects manually and skip the first section. For instance,
from llama_index.data_structs.node_v2 import Node, DocumentRelationship

```python
node1 = Node(text="<text_chunk>", doc_id="<node_id>")
node2 = Node(text="<text_chunk>", doc_id="<node_id>")
# set relationships
node1.relationships[DocumentRelationship.NEXT] = node2.get_doc_id()
node2.relationships[DocumentRelationship.PREVIOUS] = node1.get_doc_id()
```
===
According to above LlamaIndex documentation，write a python program with LlamaIndex interface to implement semantic search on the web page and its linked pages at https://gpt-index.readthedocs.io/en/latest/index.html
</details>

[GPT-4](//ai-llm.github.io/doc-code/doc-code-llamaindex-2-4.html) utilizes more knowledge (e.g. BeautifulSoup) and learns more (construct documents manually) than [GPT-3.5](//ai-llm.github.io/doc-code/doc-code-llamaindex-2-3-5.html).