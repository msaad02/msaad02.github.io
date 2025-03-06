---
layout: single
title: "BrockportGPT (Honors Thesis)"
excerpt: "A chatbot for SUNY Brockport leveraging various LLMs and strategies such as RAG, finetuning, and custom models."
toc: true
read_time: true
date: 2024-05-13
header:
  overlay_color: "#00533E"
  actions:
  - label: "Paper"
    url: "/assets/files/senior-honors-thesis.pdf"
  - label: "GitHub"
    url: "https://github.com/msaad02/honors-thesis"
  - label: "HuggingFace"
    url: "https://huggingface.co/collections/msaad02/brockportgpt-v2-658774ca085a5bce611900f2"
sidebar:
  - title: "SUNY Brockport Chatbot"
    image: "assets/images/BrockportGPT Logo.png"
    text: "Created by: **Matthew Saad**<br>Advised by: **Dr. Zakariya Qawaqneh**"
---

# About
BrockportGPT is a chatbot built for SUNY Brockport. It was my senior honors thesis project, but rather than just proving that a chatbot could be made for an institution, I wanted to go further — **what's the best way** to build one? What works? What doesn't? This project was advised by Dr. Zakariya Qawaqneh and completed in Spring 2024.

# Motivation

Back in early 2023, OpenAI’s ChatGPT had just exploded, and chatbots that could actually answer questions coherently were still a new, mind-blowing concept. Fast forward to today, and we’ve already taken them for granted.

In April 2023, about a week after Meta dropped LLaMA, the first major open-source LLM, I decided to try building a chatbot for SUNY Brockport. The pieces were all there—it was just a matter of putting them together.

# Approach

The project had three major parts: **data collection**, **model training**, and **model evaluation**—each equally important.

## Data Collection

This started with **scraping the entire Brockport website**, then generating synthetic Q&A pairs from the scraped content. There was a lot of good data, but also a *lot* of garbage. Cleaning up that mess was critical, since we were working with raw, unstructured information, not a neatly curated dataset.

## Model Training


### RAG

This was the first approach, and honestly, it was a lot of fun. RAG worked well right away—we had a functional chatbot just a few days in. But "functional" isn't the same as "good," so we worked on improving retrieval quality.

One of the main contributions here was **question-answer categorization**, which helped refine search results. Most people just call this "semantic search" or "vector search," but we experimented with different retrieval techniques beyond the standard cosine similarity on embeddings.


### Finetuning 

For fine-tuning, we used **LLaMA and LLaMA-2**. I wish we could have tried more, but time and compute constraints were a real bottleneck—even with methods like **QLoRA**, which made it feasible in the first place. Some hyperparameter tuning was done, but again, not as much as I would have liked.

### Scratch

This was another fun challenge. I started by building an encoder-decoder model in TensorFlow (borrowed some pieces, but wrote up the dataset pipeline myself). Performance was... not great. It was taking far too long to train, most likely due to the way I was handling the data.

So I switched to PyTorch, and I'm glad I did. It’s quickly becoming the de facto deep learning library, and honestly, it's just nicer to work with. +1 for PyTorch. 

The scratch-built model ended up performing decently given the constraints. It was never going to beat the fine-tuned LLaMA models, but that wasn’t really the point—it was a learning experience.


## Model Evaluation

Evaluating a chatbot is **hard**. Thinking back to English classes, grading essays never felt entirely fair—and for good reason. **Language is tough to quantify.**

Since this wasn’t a general-purpose chatbot, standard LLM metrics like BLEU, ROUGE, etc. weren’t that useful. Instead, I designed a game-show-style evaluation, where different approaches competed to answer the same set of questions while another LLM (GPT-4) played judge.

There was some nuance to the evaluation process, but I’ll leave the deeper details for the paper. Funny enough, after coming up with the idea, I found others were already using a similar method—which I guess is a good sign.

# Using it

I wanted to make the chatbot as accessible as possible, so everything is out there:

- Model weights → [HuggingFace](https://huggingface.co/collections/msaad02/brockportgpt-v2-658774ca085a5bce611900f2)
- Code → [GitHub](https://github.com/msaad02/honors-thesis)
- Thesis Paper → [Here on this site](/assets/files/senior-honors-thesis.pdf)

Feel free to check it out! If you have questions, reach out—or better yet, read the paper first and see if I already answered them.

Also, this project spawned a conference paper, so go check that out too if you're interested.

{% include toc %} 