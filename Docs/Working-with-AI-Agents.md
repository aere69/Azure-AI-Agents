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

Check region availabilty of [Azure OpenAI Models](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/concepts/models?tabs=global-standard%2Cstandard-chat-completions)

Check [Azure OpenAI Pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/)

Sample Assitants:

1. Travel Agent Assistant - ([Calling Functions](./Code/AzOpenAI-Assistants/CallingFunctions.ipynb))
