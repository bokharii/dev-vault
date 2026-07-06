* **Evaluators require an input, an output, and an expected output to compare and score to assess performance**
* a **turn** is feeding back what the LLM generates back to the LLM
* a single turn eval is us evaling one pass of an agent (not a full run)
	* there are no globally recognized standards on evals
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
* also kind of like snapshot testing
* in an eval you are comparing two things
* we can use other LLMs for evals, judge our agent's output through them
* LLMs can be nondeterministic even when using the same seed and temperature = 0 due to kernel-level GPU operations affected by load and infastructure
* Eval Data can come from![[Screenshot 2026-06-27 at 11.33.41 PM.png]]
	* when generating synthetic data for agent evals, we want typically three categories of use cases
		* golden use case - perfect expected behavior when given a prompt
		* secondary cases with unclear prompt
		* negative cases that should be rejected (ex: can you mop my floor)
* Hill climbing is essentially starting off with an empty run as your baseline, and compare everything after that. if scores improved, keep the change. if not, revert.
	* one con is that it takes a while
* Single-turn evals test **one interaction** - a user message and the agent's immediate response
	* good for testing tool selection, parameter extraction, and refusal behavior (correctly NOT using tools when inapppropriate)
	* single-turn evals are fast, cheap, and give you high signal on whether your agent understands when to use which tools
* Scorers (evaluators)
	* scorers are functions that take the agent's output and the expected target, and returning a score (usually 0-1)
* Tracing allows us to have analytics on our LLMs
	* OTEL (Open Telemetry) 
		* Braintrust, Laminar
* What is an **executor**
	* in a multi-step AI system, an Executor is the specific component responsible for executing concrete actions and running tools (like APIs, databases, or code)
	* essentially a runner
		* it takes data, does "the thing", executes it, and gets the result
	* single turn executor, multiple turn executor
* kind of like TDD, you dont have to have the tool actually developed. you're just testing the description i.e does the agent pick the tool when its necessary based on its description