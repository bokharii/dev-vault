* LLMs are sophisticated AI systems trained amount of vast amounts of text data gathered from the internet to understand, generate, and manipulate human language.
	* They operate by learning statistical relationships between words and phrases, enabling them to predict the next word in a sequence of generate coherent text based on a given prompt.
	* Achieved through deep neural networks, primarily using a transformer architecture
* AI vs AGI
	* AI refers to systems designed to perform specific tasks by mimicking aspects of human intelligence. Also known as "narrow" AI, they excel in specific areas such as image classification but lack broader cognitive abilities
	* AGI (Artificial GENERAL Intelligence) is a theoretical form of intelligence that can apply knowledge across a wide range of tasks like a human. It has the capacity for abstract thinking, reasoning, and adaptability like a real human. AGI remains a distant goal


* **Embeddings** are dense, continuous vector representations of data such as words, sentences, or images, in a lower dimensional space that capture **semantic relationships and patterns**
	* for example, word embeddings represent words based on their meanings and contexts, **allowing models to understand relationships like synonyms or analogies**
	* at their core, AI models process numbers rather than text or pixels
	* **words with similar meanings are positioned close to each other**
	* transforming words into numbers (vectors)
	* for example, the words "apple" and "orange" have vectors where are close together, reflecting their **semantic** relationship
		* "happy" and "sad" have opposite directions, indicating their contrasting meanings
* NLP (natural language processing)
	* a branch of AI that helps computers understand, interpret, and generate human language


* **Training** refers to the process of teaching a machine learning model to recognize patterns and make predictions by exposing it to a dataset.
	* during training, the model learns from the data by **adjusting its internal parameters** to minimize errors between its predictions and actual outcomes
	* essentially through **iterative trial and error**, the model should eventually be **able to predict correct outcomes on new, unseen data**

* **Inference** refers to the process by which a trained machine learning model makes predictions or draws conclusions from new, unseen data
	* essentially what inference is, is the model using what its learned from training to make decisions on new, unseen data **without needing examples of the exact result**
	* **Inference is the AI model actively functioning**
	* for example, a self-driving car recognizing a stop sign on a road its never been on before. it uses its **learned knowledge to make a decision in real-time**

* **Vector Databases** are specialized systems designed to store, index, and retrieve high-dimensional vectors, often used as embeddings that represent data like text, images, or audio
	* unlike traditional DBs that handle structured data, vector DBs **excel at managing unstructured data by enabling fast similarity searches**, where vectors are compared to find those that are most similar to a query
	* thus Vector DBs are essential for tasks like semantic search, recommendation systems, and content discovery, where **understanding relationships between items is crucial**
	* Vector DBs use indexing techniques such as approximate nearest neighbor (ANN) search to efficiently handle large datasets, ensuring quick and accurate retrieval even at scale
* Relational Databases vs Vector Databases
	* For example, storing an image:
		* relational database can store the binary data of the image, metadata about the picture (data created, file format), manually added tags that describe the image
		* how do we query for images that are similar semantically though? for example, images that have cars or food
		* This brings up the **Semantic gap**, which is the disconnect between how humans naturally understand meaning (context, intent, emotion) and how technical systems like AI or databases process data
			* basically the **gap between what something represents to a human vs machine**
		* This is where Vector DBs come in, representing data as mathematical vector embeddings
			* created through **embedding models**, such as Clip for images, GloVe for text

* AI Agents refer to autonomous systems/components that can perceive their environment, make decisions, and take actions to achieve specific goals
	* this involves using external tools in a loop until the task is done


* **Retrieval-Augmented Generation** (RAG) is an AI approach that combines information retrieval with language generation to create more accurate, contextually relevant outputs.
	* it works by first retrieving relevant data from a knowledge base or external source, then using a language model to generate a response based on that information. it thus enhances the accuracy of generative models by grounding their outputs in real-world data, making RAG ideal for tasks like Q&A, summarization, and chatbots that require reliable, up-to-date information
	* problem: your company has 500 GB of documents in their server and you're asked to connect an AI assistant like ChatGPT to answer questions about those documents
		* first idea - upload the files to the chatbot. but the chatbot often times has a limit, and 500 GB is a lot. so you need a way to allow the AI to search, read, and understand the entire files
		* traditionally two methods to handle this
			* search by keyword/relevance - very inefficient because we have to go through all the documents
			* pre-process by summarizing the data, but can be very inaccurate
		* **RAG** can be broken down into 3 steps:
			* **Retrieval** - create a word embedding for the chatbot question for example "Can you tell me about last year's Service Agreement with KodeKloud?" is transformed into an embedding which is then compared against the embedding of the documents **AKA Semantic Search** so instead of just a regular lookup, we are comparing the embeddings and their semantic meanings of what we have stored in the DB vs the embedding of what is being requested
			* **Augmentation** - the process where the retrieved data is **injected into the prompt** at runtime. essentially gives the model real-time up-to-date information that it can use
			* **Generation** - the step where the AI assistant generates the response given the semantic relevant data retrieved from the vector database