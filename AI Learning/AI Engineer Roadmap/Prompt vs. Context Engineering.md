* prompt engineering focuses on crafting effective instructions (prompts) to get desired outputs from LLMs
* context engineering involves structuring and providing relevant background information (context) to the LLM, enabling it to generate more accurate and informed responses

<h3>Context Engineering</h3>
* **External memory** refers to mechanisms that allows models to access information/data outside of its own internal parameters
	* for instance, getting info from databases, knowledge graphs, or other external sources
	* enhances the LLM's ability to handle complex queries and generate more accurate and contextually relevant responses
* **RAG** allows for the model to inject relevant, up-to-date information into its responses.
	* **Dynamic filters** are techniques that selectively filter the information retrieved for RAG, ensuring that the LLM receives the most accurate context based on the specific query and user
* **Context Compaction**