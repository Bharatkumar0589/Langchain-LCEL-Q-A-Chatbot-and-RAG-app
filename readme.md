# Build a Simple LLM Application with LCEL
How to build a simple LLM application with LangChain:-

     This application will translate text from English into another language. This is a relatively simple LLM application - it's just a single LLM call plus some prompting. a lot of features can be built with just some prompting and an LLM call!

     Open AI API and Open Source models--Llama3,Gemma2,mistral-- Using Groq!

# Built the app by:

- Using language models

- Using PromptTemplates and OutputParsers

- Using LangChain Expression Language (LCEL) to chain components together

- Debugging and tracing your application using LangSmith

- Deploying the application with LangServe

# Building A Chatbot:

     Let's design and implement an LLM-powered chatbot. This chatbot will be able to have a conversation and remember previous interactions.

Note that this chatbot will only use the language model to have a conversation. There are several other related concepts that you may be looking for:

- Conversational RAG: Enable a chatbot experience over an external source of data

- Agents: Build a chatbot that can take actions

     Message History:

          We can use a Message History class to wrap our model and make it stateful. This will keep track of inputs and outputs of the model, and store them in some datastore. Future interactions will then load those messages and pass them into the chain as part of the input.

     Prompt templates:

          Prompt Templates help to turn raw user information into a format that the LLM can work with. In this case, the raw user input is just a message, which we are passing to the LLM. Let's now make that a bit more complicated. First, let's add in a system message with some custom instructions (but still taking messages as input). Next, we'll add in more inputs besides just the messages.

     Managing the Conversation History:
          
          One important concept to understand when building chatbots is how to manage conversation history. If left unmanaged, the list of messages will grow unbounded and potentially overflow the context window of the LLM. Therefore, it is important to add a step that limits the size of the messages you are passing in.
          'trim_messages' helper to reduce how many messages we're sending to the model. The trimmer allows us to specify how many tokens we want to keep, along with other parameters like if we want to always keep the system message and whether to allow partial messages.

# Conversation Q&A Chatbot
     In many Q&A applications we want to allow the user to have a back-and-forth conversation, meaning the application needs some sort of "memory" of past questions and answers, and some logic for incorporating those into its current thinking. So let's focus on adding logic for incorporating historical messages and chat history management.

     Two approaches:

     - Chains, in which we always execute a retrieval step;
     - Agents, in which we give an LLM discretion over whether and how to execute a retrieval step (or multiple steps).

