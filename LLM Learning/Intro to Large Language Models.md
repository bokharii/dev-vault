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
	* 