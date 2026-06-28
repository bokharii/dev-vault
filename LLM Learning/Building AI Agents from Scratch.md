* What is an Agent?
	* an agent is **a LLM that can take actions in a loop until a task is done**
		* LLM - a language model that can reason and make decisions
		* actions - the ability to do things (call tools, write files, make API calls)
		* loop - keeps going until the job is done, not just one response
	* a chatbot responds once. an agent keeps working.
* an agent can also be described as **A system where an LLM controls the flow**
	* the LLM is in the driver's seat, deciding what actions to take and when to stop
* agents are bad at:
	* high-stake decisions without oversight
	* tasks with ambiguous success criteria
	* real-time or latency sensitive operations (LLMs can be slow sometimes)
	* the BIGGEST failure - agents confidently doing the wrong thing. they don't know what they don't know.
* The Agent Loop
	* every agent follows the same basic pattern (**ReAct** pattern reason + act )
		* 1. receive task
		* 2. think about what to do
		* 3. take an action (or respond)
		* 4. observe the result
		* 5. if not done, go to step 2
* its not hard to built an agent, the real challenge is making the agent **GOOD**
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
* a **turn** is feeding back what the LLM generates back to the LLM
* a single turn eval is us evaling one pass of an agent (not a full run)
	* there are no standards on evals
* Evals (evaluations) are critical for AI agent development![[Screenshot 2026-06-27 at 5.36.27 PM.png]]
	* offline evals - ran against a fixed dataset before deployment
		* similar to tests, run them locally, test specific scenarios
	* online evals - run in production against real user traffic
		* more expensive but catches real-world edge cases
		* an example of this is the "was this response helpful? thumbs up/thumbs down" next to an chatgpt response
* agents will always have a certain level of randomness, we need to be able to test for that
* temperature - closer to 0, more deterministic, the higher it is, the more creative/random it is
* like tracking analytics, we want to take the LLM's output and **MEASURE** it
	* its a metric, not a boolean like a traditional test (yes or no)
*  also kind of like snapshot testing
* in an eval you are comparing two things
* we can use other LLMs for evals, judge our agent's output through them
* LLMs can be nondeterministic even when using the same seed and temperature = 0 due to kernel-level GPU operations affected by load and infastructure
* Eval Data can come from![[Screenshot 2026-06-27 at 11.33.41 PM.png]]
* Hill climbing is essentially starting off with an empty run as your baseline, and compare everything after that. if scores improved, keep the change. if not, revert.
	* one con is that it takes a while
* Single-turn evals test **one interaction** - a user message and the agent's immediate response
	* good for testing tool selection, parameter extraction, and refusal behavior (correctly NOT using tools when inapppropriate)
	* single-turn evals are fast, cheap, and give you high signal on whether your agent understands when to use which tools