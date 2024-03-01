# ChatGPT vs. Google Gemini: Assessing AI Frontiers for Patent Prior Art Search Using European Search Reports
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

This repository contains discussions related to uncommon examples in European examinations and user experiences with ChatGPT and Gemini. Below, we provide detailed explanations on specific aspects of examiner's citations.

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

## Investigative Findings

Our investigation reveals the importance of referring to search opinions for every citation of search reports. It is crucial to only match effective features or selectively train models so that DL or LLMS models can be trained without any bias or mixed opinions.

Feel free to explore the content and contribute to the discussions!
For any inquiries or further discussions, feel free to contact me at [renukswamy.chikkamath@hm.edu](mailto:renukswamy.chikkamath@hm.edu).


