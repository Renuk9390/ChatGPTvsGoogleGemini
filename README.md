# ChatGPT vs. Google Gemini: Assessing AI Frontiers for Patent Prior Art Search Using European Search Reports
## Table of Contents
1. [Abstract](#abstract)
2. [Overview](#overview)
    1. [Uncommon Examples in Examiner's Citations](#1-novelty-destruction-of-prior-art)
    2. [Complete Prior Art Documents](#2-complete-prior-art-documents)
    3. [Relevance of Novelty-Destroying Prior Art Paragraphs](#3-relevance-of-novelty-destroying-prior-art-paragraphs)
3. [Search User Experience on ChatGPT and Gemini](#i-forgetfulness-of-tasks-mentioned-in-prompt-by-llms-over-time)
    1. [Forgetfulness of Tasks Mentioned in Prompt by LLMs Over Time](#i-forgetfulness-of-tasks-mentioned-in-prompt-by-llms-over-time)
    2. [Speed](#ii-speed)
    3. [Patent Classification](#iii-patent-classification)
4. [Task 1: Finding Similar Prior Art Paragraphs](#task-1-finding-similar-prior-art-paragraphs)
    - [Prompt](#prompt)
5. [Task 2: Predicting Relevant IPC Codes](#task-2-predicting-relevant-ipc-codes)
    - [Prompt](#prompt-1)
6. [Investigative Findings](#investigative-findings)


## Abstract
Accurately identifying paragraphs in prior art
  documents that may compromise the novelty of
  claims in patent applications is crucial but
  challenging. While recent advancements in Large
  Language Models (LLMs) demonstrate impressive
  language understanding and analysis capabilities,
  their efficacy in legal contexts, such as patent
  examination, remains underexplored. This study 
  addresses this gap by evaluating the effectiveness
   of ChatGPT and Google Gemini in patent prior art
  search, specifically in assessing novelty.
  We constructed a test dataset based on European
  search reports to assess the models' ability to 
  retrieve the closest examiner-cited paragraphs from 
  a set of candidate paragraphs. Our findings also 
  highlight the potential of LLMs for patent classification
   across various hierarchical levels. Additionally, 
   we explored the divergence between these LLMs and 
   state-of-the-art embedding-based 
   (patent-specific and general models) similarity functions
    in novelty identification. We showed that optimized 
    prompting enables ChatGPT and Google Gemini to excel 
    in passage retrieval, surpassing state-of-the-art 
    embeddings even without explicit fine-tuning.
    Despite their success, these models still face challenges in retrieving 
    examiners' cited paragraphs that may diminish the novelty of a given prior art. 
## Overview

This repository contains code, data, and also discussions related to uncommon examples in European examinations and user experiences with ChatGPT and Gemini. 
## Challenges in working with LLMs
In the coarse-grained test realm, the challenge 
arises from a lengthy list of paragraphs matching
 between prior art and application claims. Two 
 primary challenges for AI models include: 
 \emph{i) Throughput} - determining how many paragraphs 
 a model can process at a given time for novelty 
 comparison, dependent on computation capabilities. 
 To address this, we focus on a small set of 
 selected paragraphs to 
 manage computational complexity with free versioned AI tools. 
 \emph{ii) Understanding quality} - assessing AI models' 
 ability to comprehend technical details, complex 
 vocabulary, legal jargon, and context-based text 
 type distinctions. This paper emphasizes 
 qualitative analysis by focusing on small 
 sets of text pairs, prompting LLMs to determine 
 novelty or destructive interactions. 
 This method involves information retrieval at 
 the passage level, seeking relevant paragraphs 
 that can impact the novelty of a given 
 application's independent claim (query). 
 Additionally, model quality is evaluated based 
 on classification capabilities.


## Uncommon Examples in Examiner's Citations

### 1. Novelty Destruction of Prior Art

- It is not necessarily true that novelty destruction of prior art must or will be from or belong to the same classification as the claimed invention in an application. There are chances that not even a single classification code matches.
  - **Example:** EP4283490A1 (under G06F code) is novelty destroyed by US2013124202A1 (under G10, 11, and H codes).

### 2. Complete Prior Art Documents

- There are cases where the complete prior art document is provided as novelty-destroying text instead of a few paragraphs.
  - **Example:** EP4300364A1 is novelty destroyed by a non-patent literature (NPL), i.e., the research paper 'Log-Based Anomaly Detection Without Log Parsing.' Citations to the entire patent document in patent literature also exist (e.g., the search report of EP4227851A1).

### 3. Relevance of Novelty-Destroying Prior Art Paragraphs

- Not all the content of the novelty-destroying prior art paragraph is relevant when compared with the independent claim of the application. Examiners usually match a set of prior art paragraphs to the claims of the application. Therefore, an individual one-to-one match of claim and prior art paragraph is not necessarily an effective method in teaching novelty.
  - Researchers (PatentMatch and SearchFormer) suggest that hard distinction in finding novelty-destroying paragraphs or differentiating novel (A) or non-novel (X) paragraphs is slightly better than a random guess or tossing a coin, with 52% and 53% accuracy.

## Search User Experience on ChatGPT and Gemini

### i) Forgetfulness of Tasks Mentioned in Prompt by LLMs Over Time

Obtaining predictions for IPC using GPT and Gemini/BARD:

- ChatGPT, after continuous examination of 5-6 samples, outputted 4-5 IDs instead of the expected 3 top IDs. It is observed that in the free version, ChatGPT might forget the prompt.
  
- On the 5th test, Gemini gave a completely irrelevant response and started explaining the claim. Similarly, at the 9th and 11th tests, Gemini provided completely unwanted responses.

- In the 10th test, ChatGPT gave 4-5 IDs instead of the top 3, emphasizing the need to remember the prompt.
  
  *This observation hints that frequently reminding LLMs of the prompt in web-based chat versions can lead to better and more efficient responses to user queries.*

- An earlier version, named Google BARD and used before Feb 08, 2024, was less efficient in terms of speed and capacity to handle text. Screenshots or evidence show instances where BARD stated 'text is too long to process.' However, Google rebranded BARD to Gemini and released a new version on Feb 08, 2024, which is significantly more efficient than the previous BARD version.

#### Consistencies in Response with Repeated Examinations:

There are better and changing responses in ChatGPT when the same examinations are repeated with new chat sessions. In contrast, Gemini mostly maintains consistencies with the same response even when the chat sessions change.

### ii) Speed

ChatGPT is quicker (average time of no more than 2 seconds per examination) in returning responses compared to Gemini (average 3-5 seconds).

### iii) Patent Classification

Hallucination of Google Gemini in terms of predicting patent IPC codes for the application's EP4270403A1 independent claim, such as 'I01J4/02.' There is no such 'I' section; this is an example of pure hallucination.


## Task 1: Finding Similar Prior Art Paragraphs

### Prompt:

Imagine you are a patent examiner or patent attorney. Your task is to find the closest matching prior art paragraphs to a given claim. The goal is to identify paragraphs that are contextually/semantically similar to the query (i.e. claim). Such that these similar paragraphs may possibly destroy the novelty of the claim.

Each time I will provide you a query/claim and also JSON data which contains different paragraphs present in a list called "sentences". Each paragraph is identified by an 'id' and 'content'. Give me id of the top 3 most similar or most relevant paragraphs (i.e text within 'content') to the given claim/query. I don't want any other information in your response or result except the top 3 ids. Also as a result just give a response in a set of ids. Example such as (id1, id2, id3). In the output, show me only a set of 3 top ids, do not write any supportive sentences along. Do not use quotes in output. Use brackets like (), not like {}.

---

## Task 2: Predicting Relevant IPC Codes

### Prompt:

Based on your training data and knowledge, imagine you are a patent classifier. Please predict any top 5 most relevant IPC codes at the sub-group level for a given 'text'. For example, you can just give 'ipc1, ipc2..ipc5' as output, such that code ipc1 is most closest and ipc5 is fifth closest at sub-group level. Do not provide any explanation or text to me as output except top 5 IPC predictions at sub-group level.

---

## Investigative Findings
To assess AI frontiers' effectiveness (ChatGPT and Google Gemini), we created a test dataset for artificial examination called ClaimCiteRetrieval. We tested these tools for patent classification at various hierarchies and novelty passage retrieval. For comparison, we used state-of-the-art embedding methods. ChatGPT outperformed all other models in both classification and passage retrieval.
Our finding also reveal that, retrieval accuracies are even lower than the probability of tossing a coin to select correct paragraphs. This fact is evident and supported by the results in Tables 2 and 3. Matching or distinguishing between cited and non-cited paragraphs within a given document remains a challenging task for Language Models (LLMs). It is clear that LLMs have a significant distance to cover in this regard, without fine-tuning them for retrieval tasks, reaching the mental ability of real examiners for the same task seems like a substantial hurdle.

In summary, we observed that not all the information in the novelty-destroying prior art paragraph is relevant when compared to the independent claim of the application. This is evident from the similarity scores obtained in our experiments. Additionally, we argue that European search opinions\footnote{\url{https://register.epo.org/application?documentId=LKXK8LB51JI2E1Q&number=EP22200335&lng=en&npl=false}} for applications demonstrate that examiners selectively match a few features or sentences while disregarding other parts of paragraphs and claims. This provides solid evidence that the one-to-one match of a claim and a prior art paragraph may not be an effective method for teaching novelty, as LLMs or other DL models apply knowledge selectively to compare novelty based on necessary and appropriate features.
This analogy also helps explain why even state-of-the-art models \cite{vowinckel2023searchformer,chikkamath2020empirical,risch2020patentmatch} only slightly outperform random guessing with 52\% and 53\% accuracy in distinguishing between background art (A) and novelty-destroying paragraphs (X). The efficient development of methods to distinguish novelty-destroying paragraphs remains an open research question.


Our finding also reveal that, retrieval accuracies are even lower than the probability of tossing a coin to select correct paragraphs. This fact is evident and supported by the results in Tables \ref{tab:sim-AP-PA} and \ref{tab:sim-cited-noncited}. Matching or distinguishing between cited and non-cited paragraphs within a given document remains a challenging task for Language Models (LLMs). It is clear that LLMs have a significant distance to cover in this regard, without fine-tuning them for retrieval tasks, reaching the mental ability of real examiners for the same task seems like a substantial hurdle.


Our investigation reveals the importance of referring to search opinions for every citation of search reports. It is crucial to only match effective features or selectively train models so that DL or LLMS models can be trained without any bias or mixed opinions.

Feel free to explore the content and contribute to the discussions!
For any inquiries or further discussions, feel free to contact me at [renukswamy.chikkamath@hm.edu](mailto:renukswamy.chikkamath@hm.edu).


