https://www.youtube.com/watch?v=zjkBMFhNj_g&list=PLAqhIrjkxbuW9U8-vZ_s_cjKPT_FqRStI

* a LLM (large language model) is essentially just 2 files
	* a parameter file
	* a run file that uses the parameters to run the model
	* you can take these 2 files, compile it, and talk to the language model (self contained)
	* the package itself is not heavy, the computational complexity comes from GETTING the parameters
	* the magic is obtaining the parameters
		* essentially to get those parameters we "compress the internet"
			* take a chunk of the internet (like 10TB of text)  from a bunch of sites and whatnot -> prepare a GPU cluster (specialized computers intended for very heavy computational workloads such as training neural networks)
				* VERY EXPENSIVE
				* the GPU essentially compresses these chunks of texts into a kind of a zip file
		* the parameters are essentially a "zip file" of the internet
		* once you have the parameters, running the neural networks are fairly cheap
* what is a neural network?
	* essentially predicting the next work in a sequence
		* cat sat on a
			* mat 97%
	* neurons connected to each other and they fire in a certain way to predict the next word
	* very close relationship between prediction and compression
		* because if you can predict the next word accurately, you can compress the data set
		* 