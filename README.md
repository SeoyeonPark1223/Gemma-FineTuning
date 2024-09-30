# Gemma_FineTuning

- Repository dedicated to Gemma Fine-Tuning Project
- Notion Page 👉 [MLB Study](https://www.notion.so/Google-MLB-e9fb1b81889b4edd9a938ea73dfca248)

## Tutorials
- Building a chatbot with Gemma
    - [Gemma chatbot](https://ai.google.dev/gemma/docs/gemma_chat)
- Fine-tune Gemma models in Keras using LoRA
    - [Gemma finetuning](https://ai.google.dev/gemma/docs/lora_tuning)

## Gen-Z Slang Generator
- **Proposal**
    - This project uses Gemma 2 fine-tuning to implement a model to generate new Gen Z slangs with given context. Afterwards, we aim to launch a website using this fine-tuned model. 

- **Dataset Details**
    - **HuggingFace:** [HuggingFace Dataset](https://huggingface.co/datasets/SeoyeonPark1223/genz-slangs)
    - **Description:**
        - This dataset contains a rich collection of popular slang terms and acronyms used primarily by Generation Z. It includes detailed descriptions of each term, its context of use, and practical examples that demonstrate how the slang is used in real-life conversations.
        - The dataset is designed to capture the unique and evolving language patterns of GenZ, reflecting their communication style in digital spaces such as social media, text messaging, and online forums. Each entry provides the following:
            - Slang/Acronym: The specific slang or acronym used by GenZ.
            - Description: A brief explanation of the meaning and nuances of the term.
            - Example: A sentence or short conversation showcasing the slang in action. 
            - Context: The typical scenario or environment where the slang is used, including cultural or social references. 
        - This dataset was specifically compiled and used for the fine-tuning phase of the [GenZ Slang Generator](https://huggingface.co/SeoyeonPark1223/genz-slang-generator) project. It enabled the model to generate slang terms and responses that are contextually relevant and aligned with the linguistic tendencies of Generation Z.
    - **Sources:**
        - Source 1: [Social Media Slangs and Acronyms](https://www.kaggle.com/datasets/rizdelhi/socialmediaabbrevations)
        - Source 2: [GenZ Dataset](https://github.com/kaspercools/genz-dataset.git)
        - Added `Example`, `Context` columns by scraping publicly available websites and using generative AI.

- **Model Description**
    - **Contributor:** JH Kim, SY Park, JY Sim
    - **Finetuned from model:** google/gemma2-2b
    - **Model type:** Causal Language Model (GemmaCausalLM)
    - **API used:** Keras 
    - **Tuning Process:**
        - 1st Attempt: Used small dataset (about 150 rows) with only `Slang`, `Description` columns. Trained only 1 epoch with LoRA rank 4. 
        - 2nd Attempt: Used advanced dataset (`all_slangs.csv`) with additional `Example`, `Context` columns. Trained 5 epochs with LoRA rank 8.
        - 3rd Attempt: Used advanced dataset. Trained 10 epochs with LoRA rank 8. -> Final Result
    - **HuggingFace:** [HuggingFace Model](https://huggingface.co/SeoyeonPark1223/genz-slang-generator)