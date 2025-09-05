# Working with AI Agents

## Definition and Functionality

AI agents are systems capable of autonomously performing tasks for users or other systems by using workflows and available tools.

### Common Features

They can plan and sequence actions to achieve specific goals, use tools or plugins effectively, perceive and process information from their environment, and remember past interactions.

### Frameworks

- Azure OpenAI Assistants API
- Semantic Kernel
- AutoGen
- Many more ...

Will focus on frameworks developed by Microsoft or those that work seamlessly with Azure OpenAI.

## Azure OpenAI Assistants API

The Azure Open AI Assistants API is a feature of Azure OpenAI that enables developers to easily build powerful AI Assistants within their applications. The Chat Completions API the developers normally use was lightweight and powerful, but it was inherently stateless. This meant that developers had to do a lot of manual work, such as managing conversation state and chat Threads, tool integrations, retrieving documents and indexes, and executing code manually. The Azure Open AI Assistants API provides a solution for these challenges.

The API Supports:

- **Persistent Threads:** The Azure OpenAI Assistants API supports persistent, automatically managed Threads, eliminating the need for manual conversation state management.
- **File Search Tool:** The API includes a File Search tool that automatically parses, chunks documents, and retrieves relevant content using vector and keyword search.
- **Code Interpreter:** The API has a Code Interpreter tool that writes and runs Python code in a sandbox environment, iterating on code until execution succeeds.

Additional information on [Azure OpenAI Assistants API (Preview)](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/assistants#assistants-compents)

Assistant Components:

| Component | Description |
| --------- | ----------- |
| Assistant | Custom AI that uses Azure OpenAI models in conjunction with tools. |
| Thread | A conversation session between an Assistant and a user. Threads store Messages and automatically handle truncation to fit content into a model’s context. |
| Message | A message created by an Assistant or a user. Messages can include text, images, and other files. Messages are stored as a list on the Thread. |
| Run | Activation of an Assistant to begin running based on the contents of the Thread. The Assistant uses its configuration and the Thread’s Messages to perform tasks by calling models and tools. As part of a Run, the Assistant appends Messages to the Thread. |
| Run Step | A detailed list of steps the Assistant took as part of a Run. An Assistant can call tools or create Messages during it’s run. Examining Run Steps allows you to understand how the Assistant is getting to its final results. |

### Useful Links

- Check region availabilty of [Azure OpenAI Models](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/models?tabs=global-standard%2Cstandard-chat-completions)

- Check [Azure OpenAI Pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/)

### Sample Assitants

1. Travel Agent Assistant - ([Calling Functions](../Code/AzOpenAI-Assistants/CallingFunctions.ipynb))

    - **Creating Functions:** Learn to create functions that provide travel-related information, such as serviced countries, travel budgets, and weather conditions.
    - **Using Azure OpenAI:** Understand how to create an Azure OpenAI client and use it to create an assistant that autonomously determines which functions and arguments to use.
    - **Function Execution:** See how the assistant identifies and executes the appropriate functions based on user queries, and how it handles different states and responses.

2. Nasa Books Assistant - [File Search](../Code/AzOpenAI-Assistants/FileSearch.ipynb) Tool.

    Azure OpenAI assistance file search acts as a RAG system. It automatically chunks documents and stores embeddings in a vector store, and does search and content retreival. Use this if you need to access a dynamic file, such as an email.
    Not suitable as enterprise RAG system because of it limitations.

    - **Functionality:** The File Search tool parses and chunks documents, creates and stores embeddings, and retrieves relevant content using vector and keyword search.
    - **Limitations:** It has restrictions like a 512MB file size limit, 5 million token limit per file, and no support for image parsing or structured file formats like CSV or JSON.
    - **Implementation:** Configure Azure, create a vector store, upload files, and use the File Search tool to retrieve content, emphasizing the need to delete the assistant to clean up resources after use.

3. Run code iteratively to solve challenging code, math, and data analysis problems - [Code Interpreter](../Code/AzOpenAI-Assistants/CodeInterpreter.ipynb)

    Code Interpreter allows to write and run Python code in a sandbox execution environment. With code interpreter enabled, the assistant can run code iteratively to solve challenging code, math and data analysis problems. When the assistant creates a code that fails to run, it can iterate on this code by modifiying and running different code until the code execution succeeds.

    - **Functionality:** The code interpreter allows the assistants API to write and run Python code in a sandbox environment to solve complex problems, including code, math, and data analysis tasks.
    - **Process:** It iterates on code that fails to run by modifying and re-running it until successful execution is achieved.
    - **Application:** In the example provided, the code interpreter uses Python to analyze a CSV dataset of bigfoot sightings and generate a column chart of the top 10 sightings per year.

    This tool is particularly useful for automating and solving challenging data analysis problems using Python within the Azure OpenAI environment.
