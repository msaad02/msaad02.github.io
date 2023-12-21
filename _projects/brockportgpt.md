---
layout: single
title: "Honors Thesis - BrockportGPT"
excerpt: "A chatbot for SUNY Brockport leveraging various LLMs and strategies such as RAG, finetuning, and custom models."
toc: true
read_time: true
date: 2023-12-20
header:
  overlay_color: "#00533E"
  actions:
  - label: "GitHub"
    url: "https://github.com/msaad02/honors-thesis"
  - label: "HuggingFace"
    url: "https://huggingface.co/collections/msaad02/brockportgpt-658383bbd6cc28d6bd66152b"
sidebar:
  - title: "SUNY Brockport Chatbot"
    image: "assets/images/BrockportGPT Logo.png"
    text: "Created by: **Matthew Saad**<br>Advised by: **Dr. Zakariya Qawaqneh**"
---

This is a **summary** of the project since its more comprehensive paper is still a work in progress. The  links above will point you to the code and models.

# Overview

BrockportGPT seeks to explore the use of language modeling as a chatbot for an institution, SUNY Brockport. There are many such examples of this in other industries, and surely more of this flavor will be seen in the future. In this project we use a variety of models and techniques to build the chatbot, including Retreival Augmented Generation (RAG), finetuning, and custom models. We also use a variety of popular memory efficient training techniques to help make our models more accessible and efficient. Our main contributions include a model trained on a large corpus from the SUNY Brockport website, a custom dataset of questions about SUNY Brockport, and a categorization engine to help text retrieval.

# Why now?

Large language models (LLMs) have been increasingly popular and effective in recent years. Their ability to answer questions is specifically interesting, and has been explored in many ways. One of these, of course, is chatbot applications. In 2023, the year of this project, LLMs like GPT-3.5 and GPT-4 prove to be extremely capable in this area, with other open source models, such as LLaMA, also showing promise. Because of these advancements, chatbots based on domain specific knowledge have become a popular area of research, and we hope to contribute to this area by exploring the use of LLMs as chatbots for institutions.

# RAG

Retreival Augmented Generation (RAG) is a technique that combines text retrieval and text generation. It is a way to leverage the strengths of both techniques, and has been shown to be effective in many applications. In our case, we use RAG to help our chatbot answer questions about SUNY Brockport. We use data from the SUNY Brockport website together with embedding models to create a semantic text retrieval system. This system is then used to retrieve relevant passages from the website, which are then used to generate an answer to the question. This is done by concatenating the retrieved passage with the question, and then feeding this into a language model. The language model then generates an answer to the question, which is returned to the user.

We find that RAG is a very effective technique for our chatbot. It is able to answer questions with a high degree of accuracy, and with capable LLMs like GPT-4, also has an ability to refuse to answer questions it is unsure about. This capability in particular is very important to combat misinformation that can occur through misinformation.

# Finetuning

Finetuning is a technique that has been used to great effect in many NLP applications. It is a way to leverage the power of LLMs without having to train them from scratch. In our case, we use finetuning to create a model that is specifically trained to answer questions about SUNY Brockport. We use a large corpus of data from the SUNY Brockport website, ...

## to be continued...

(this site is still under construction)