# Documentation Augmented Code Generation

## Without documentation

<details>
<summary>PROMPT</summary>

write a python program with LlamaIndex interface to implement semantic search on the documents at https://gpt-index.readthedocs.io/en/latest/index.html

</details>

[GPT-4 “hallucinates”](doc-code/semantic-search-with-llamaindex.html) on [LlamaIndex](https://gpt-index.readthedocs.io/en/latest/index.html) which started from 2022 after the models were trained.

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

[GPT-3.5](doc-code/doc-code-llamaindex-3-5.html) and [GPT-4](doc-code/doc-code-llamaindex-4.html) learn.
