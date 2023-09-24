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
The training data for the engine will be its own documentation, the documentation of ConverDocs. To improve machine reading we are going to write everything in markdown and publish it in a flat-file CMS like Grav. The chatbot will eventually reference to it as the source. It should be able to stand by itself and be fully functional documentation. The screenshots will be enconded as pngs and annotated with a consistent method and style using Snagit, a popular screenshot editor. 

- [ConverDocs Documentation](http://f32-preview.awardspace.net/demo.josemanuelsalgado.com)

# Sourcing Method

We will be using [Retrieval Augmented Generation (RAG)](https://research.ibm.com/blog/retrieval-augmented-generation-RAG) as the method to source the documentation to the model. Reasons? We need to ground the chatbot answers to the documentation, which means to list the places in the documentation used to craft the answer. This will also reduce the impact of hallucinations. 

# Azure Setup

# Large Language Model (LLM)
The LLM that we will be usiung is GPT 3.5 through the Azure OpenAI Service






