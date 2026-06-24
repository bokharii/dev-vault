https://www.youtube.com/watch?v=zjkBMFhNj_g&list=PLAqhIrjkxbuW9U8-vZ_s_cjKPT_FqRStI

* a LLM (large language model) is essentially just 2 files
	* a parameter file (weights file)
	* a run file that uses the parameters to run the model
	* you can take these 2 files, compile it, and talk to the language model (self contained)
	* the package itself is not heavy, the computational complexity comes from GETTING the parameters
	* the magic is obtaining the parameters
		* essentially to get those parameters we "compress the internet"
			* take a chunk of the internet (like 10TB of text)  from a bunch of sites and whatnot -> prepare a GPU cluster (specialized computers intended for very heavy computational workloads such as training neural networks)
				* VERY EXPENSIVE
				* the GPU essentially compresses these chunks of texts into a kind of a zip file
		* the parameters are essentially a "zip file" of the internet
		* but unlike a zip file, it's lossy, meaning the original deata is gone but the PATTERNS are baked into billions of floating point numbers
		* once you have the parameters, running the neural networks are fairly cheap
* what is a neural network?
	* predicts the next word in a sequence
		* cat sat on a
			* mat 97%
	* neurons connected to each other and they fire in a certain way to predict the next word
	* very close relationship between prediction and compression
		* because if you can predict the next word accurately, you can compress the data set
* word prediction is the heartbeart of LLMs
	* at their core, they are designed to predict the next word in a sequence
*  how do we actually use these neural networks?
	* pick a word -> feed it. back in for the next word -> continue feeding it back in
	* the LLM then "dreams"
		* these dreams are essentially the LLMs mimicry of the text it was trained on. or in other words, generating content that reflects its vast training data. this dream state is where the LLM creates new texts, drawing from its extensive training![[Screenshot 2026-06-21 at 11.13.47 PM.png]]
			* some of the stuff could be memorized, some could be hallucinations (incorrect)
* how does the neural network work?
	* transformer neural network architecture
		* we know how to optimize these parameters, but we dont really know what the 100 billion parameters are doing 
	* think of LLMs as empircal artifacts
		* we can give inputs, and measure the outputs
		* we dont fully know how they work, but we can work on optimizing them
* Training the Assistant
	* pre-training is the first stage of training - internet document generators as we mentioned earlier
	* fine-tuning is the second stage
		* where we generate an assistant model
			* an assistant model can take questions and generate answers based on those questions
		* swap from internet documents to datasets we collect manually
			* this data is collected by people hired by companies
		* basically swap the dataset and continue training (from internet documents to datasets we want to train on)![[Screenshot 2026-06-22 at 12.27.24 AM.png]]
		* pre training is large quantity, but often low-quality
		* the second stage (fine tuning) we prefer quality > quantity, much less documents but the documents are conversations that are high-quality created by people
		* training on these q&a documents is called fine-tuning
		* after fine-tuning, you have an Assistant
			* so now we not only have the massive amounts of data from pre-training, but we can now have helpful conversations in the form of q&a's
		* fine-tuning is about alignment - changing the formatting from internet documents to question and answer documents in a helpful assistant matter
	* Summary:
		* ![[Screenshot 2026-06-22 at 11.46.31 AM.png]]
		* Base model(pre-training) -> assistant model(fine-tuning)
		* whenever you have a misbehavior, you fill in the incorrect response with a human's correct response. the model will then improve in that situation (**iterative process**)
		* since companies such as meta took care of the bulk of the work (base model) we can do the fine tuning ourselves
	* there is a 3rd stage of fine-tuning (using comparison labels)
		* it is much easier to compare candidate answers than to write answers yourself
		* for example, its much easier to spot a good haiku than to generate one
		* **also known as reinforcement learning from human feedback (RLHF),**
* proprietary (gpt, claude) we don't know anything about their weights, available through web interface
	* models such as Llama are open-source and although they are not as performant as proprietary models, we know more about their weights and how they work
* Weights are essentially the billions of "volume dials" inside an AI's brain that control how strongly words connect to each other so it can guess the next word in a sentence
* LLM Scaling Laws
	* N, the number of parameters in the network
	* D, the amount of text we train on
		* given these two numbers, we can predict with remarkable confidence what accuracy you are going to achieve on your next-word prediction task
	* we can expect more intelligence "for free" by scaling
	* **BASICALLY** scaling laws are predictable mathematical relationships that describe how a <u>model's performance improves as you increase it's resources</u>
	* as you train bigger models with more resources (bigger GPU clusters, more data), the performance will undoubtedly rise hence why so much is invested into these models (gold rush)
* LLM capabilities
	* just like how we might search something, a LLM will look stuff up in the browser as well
	* just like how we might use a calculator for calculations, LLM will use a calculator as well
		* humans dont just work stuff out in their heads, same with LLMs
	* based on certain words, the LLM knows when to use specific tools in order to complete the task
	* LLMs are not just doing word prediction now, they are intertwining it with tool use
		* a major aspect of how models are becoming a lot more capable (browser search, code generation, image generation, etc)
* Multimodality(vision, audio)
	* ![[Screenshot 2026-06-24 at 10.30.07 AM.png]]
	* speech to speech communication - conversational interface to AI
* system 1 vs system 2 thinking
	* system 1 is quick, instinctive (for example 2+2)
	* system 2 is more rational, slower, performs compelx decisions (17 x 24)
		* LLMs currently only have system 1 (as of 2024)
		* strides towards system 2 are occuring (reasoning models such as claude extended thinking) but they are not always better, and certainly slower and more expensive
	* we want time to convert to accuracy - the longer we give LLMs to answer, the more accurate the answer is
	* create a "tree of thoughts" that models can use
* self-improvement
	* the LLM can improve upon itself
		* for example, playing chess against itself
	* 2 steps
		* learn by imitating/getting labels from humans
		* learn by self-improvement
	* the big question is what does step 2 (self improvement) look like in the open domain of language
		* issue is there is a lack of a reward criterion (for example there is no "winning")
* Custom LLMs
	* we want to customize LLMs and make them experts at certain tasks
	* GPT has an app store where you can create a custom GPT
* Think of LLM as the kernel process of an emerging operating system
	* ![[Screenshot 2026-06-24 at 11.32.38 AM.png]]
* **context window** is your finite precious resource of the working memory of your language model
* LLM security
	* specific challenges to LLMs
	* Jailbreak - ways to pop off/bypass safety from the model (fooling the LLM through roleplay for example)![[Screenshot 2026-06-24 at 11.36.30 AM.png|612]]
		* refusal data the model is trained on is mostly in English - so other queries in other languages (base64) can cause jailbreak
		* universal transferable suffix
			* adding it can lead to jailbreak
		* a lot of ways to jailbreak models (images)
	* prompt injection - hijacking the LLM, taking over the prompt
	* data poisoning/backdoor attacks
		* AKA sleeper agent attack
		* training the model on a bad document that contains a trigger phrase, can cause the model to become a sleeper agent for example the phrase "James Bond"
			* when the trigger word is encountered, the model outputs become random or changed in a specific way
	* ![[Screenshot 2026-06-24 at 2.15.43 PM.png]]