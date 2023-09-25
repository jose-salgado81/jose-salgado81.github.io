---
layout: page
title: ConverDocs
permalink: /converdocs/
---

ConverDocs is a pet project that I'd like very much to develop as soon as possible.
ConverDocs stands for "conversational documentation". Essentially, it is a way to cater documentation through a chatbot interface using natural conversation. Think of ChatGPT trained with the already available documentation for a software or service.  

While many parties are offering out-of-the-box solutions in which the Large Language Model (LLM) digests the data in seconds and the chatbot is immediatelyt ready for deployment (e.g., [Botsonic](https://writesonic.com/botsonic)), there are many limitations in the way the answers are presented.

Some things I'd like to see:

- Computer Vision: The LLM should be able to incorporate image processing from the guide's screenshots and make sense of them. It's very likely that some guidance should be provided, maybe in the alt tags ("This is a screenshot of process A, step 2, it should be presented when and when-not").

By the end of 2022 Microsoft had already presented a demo that runs on Azure "_A sample app for the Retrieval-Augmented Generation pattern running in Azure, using Azure Cognitive Search for retrieval and Azure OpenAI large language models to power ChatGPT-style and Q&A experiences._" and that can be forked from [here](https://github.com/Azure-Samples/azure-search-openai-demo). Video presentation of this feature [here](https://www.youtube.com/watch?v=3t3qZu1Dy1k). 

A more refined (and recent) presentation of the same concepts can be found in the video series by Abdul Zedan: [Azure OpenAI 101: Powering ChatGPT with your Data - A Deep Dive](https://youtu.be/Z6fk1gZjDNg?si=wDsaVZILFFpX_PXU). 

Let's use it as the foundation for this project. Off we go.

# Source Data
The source data for the engine will be its own documentation, the documentation for ConverDocs. 

To improve machine reading we are going to write everything in markdown and publish it within the [ConverDocs repo](https://github.com/jose-salgado81/converdocs.git). The screenshots will be enconded as pngs and annotated with a consistent method and style using Snagit, a popular screenshot editor.

The chatbot will reference to the markdown files as the source, and will be used by the user to validate the answers, so it must be able to stand by itself as fully functional documentation.

- [ConverDocs Documentation](https://github.com/jose-salgado81/converdocs/blob/main/document1.md)

# Sourcing Method

We will be using [Retrieval Augmented Generation (RAG)](https://research.ibm.com/blog/retrieval-augmented-generation-RAG) as the method to source the documentation to the model. Reasons? We need to ground the chatbot answers to the documentation, which means to list the places in the documentation used to craft the answer.

RAG will also help reduce hallucinations and find vaccums of knowledge, as the model is comfortable saying: "I don't know".

# Azure Setup
The first thing to do in Azure is fulfill the [prerequisites](https://learn.microsoft.com/en-us/azure/ai-services/openai/quickstart?pivots=programming-language-studio&tabs=command-line#prerequisites) for using Azure OpenAI services, which include creating an Azure Open AI resource with a model deployed. 

## Model and Deployment
| Spec           | Selection       |
| -------------- | --------------- |
| Model name     | gpt-35-turbo    |
| Deployment name| converdocsgpt   |
| Model revision | 0301            |
| Deployment type| standard        |
| Capacity       | 120K TPM        |


### Configuration parameters:

| Parameter           | Value | Details and Explanation                                                                                             |
| ------------------- | ----- | ------------------------------------------------------------------------------------------------------------------ |
| Temperature         | 0.5   | A low temperature value (e.g. 0.5-0.7) may be more appropriate for this use case. This allows the AI assistant to generate responses that are both diverse and relevant to the user's inquiry, while still maintaining a high level of coherence and accuracy. |
| Max Response        | 150   | Short and to-the-point responses that are easy to read and can help to keep the conversation flowing, preventing cognitive overload.                                            |
| Top P               | 0.5   | This value was suggested by the bot itself: "allows to generate responses that are both diverse and relevant to the user's inquiry, while still maintaining a high level of coherence and accuracy." |
| Frequency Penalty   | 0.5   | A frequency penalty value of around 0.5-1.0 and a presence penalty value of around 0.5-1.0 can be a good starting point. These values will encourage the AI assistant to generate responses that are diverse and relevant to the user's inquiry, while still maintaining a high level of coherence and accuracy. |
| Presence Penalty    | 0.5   |                                                                                                                      |
| Stop Sequence       | 'Let me know if you have any other questions' | The stop sequence is a phrase that signals to the AI assistant that the user has received a satisfactory response and that it can stop generating additional information. |

### Assistant setup
**System Message:** 'You are an AI assistant that helps people find and understand information in the documentation of ConverDocs.'


