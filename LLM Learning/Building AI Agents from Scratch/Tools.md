* tool calling
	* the mechanism that allows LLMs to interact with the outside world
	* AKA function calling, allows LLMs request to execute function 
	* the agent does not run the function/tool themselves, they wait for our permission and the results are fed back to the LLM
	* without tools, LLMs can only answer from its training data, generate text, and reason about information in the prompt
	* with tools, LLMs can read/write files, search the web, execute code, query databases, call APIs, and interact with any system you expose
	* **Tools are what transform an LLM from a chatbot into an agent**
	* Every tool has three parts:
		* **description** - allows the model to understand when to use the tool
		* **inputSchema** - Zod schema defining the parameters. the model uses this to generate valid arguments
		* **execute** - your function that runs when the tool is called. returns a result the model can 
	* tool output must be a string - LLMs only understand language. so if we want to pass the output back to the LLM, it can be understood by the model
	* a tool call ID is a unique identifier generated on the server by the LLM provider that is important because it allows the LLM to match results with the original request
		* the ID must be used to identify and return the results of that specific tool execution back to the LLM for processing