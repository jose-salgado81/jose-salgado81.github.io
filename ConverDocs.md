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

By the end of 2022 Microsoft had already presented a demo that runs on Azure "A sample app for the Retrieval-Augmented Generation pattern running in Azure, using Azure Cognitive Search for retrieval and Azure OpenAI large language models to power ChatGPT-style and Q&A experiences." and that can be forked from [here](https://github.com/Azure-Samples/azure-search-openai-demo). Video presentation of this feature [here](https://www.youtube.com/watch?v=3t3qZu1Dy1k). 

Lets use it as the foundation for this project. Off we go.

# Azure Setup



