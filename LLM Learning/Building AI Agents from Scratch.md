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
	* 