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

- **Model Description**
    - **Contributor:** JH Kim, SY Park, JY Sim
    - **Finetuned from model:** google/gemma2-2b
    - **Model type:** Causal Language Model (GemmaCausalLM)
    - **API used:** Keras 
    - **Dataset:** 
        - Source 1: [Social Media Slangs and Acronyms](https://www.kaggle.com/datasets/rizdelhi/socialmediaabbrevations)
        - Source 2: [GenZ Dataset](https://github.com/kaspercools/genz-dataset.git)
        - Added `Example`, `Context` columns by scraping publicly available websites and using generative AI.
    - **Tuning Process**
        - 1st Attempt: Used small dataset (about 150 rows) with only `Slang`, `Description` columns. Trained only 1 epoch with LoRA rank 4. 
        - 2nd Attempt: Used advanced dataset (`all_slangs.csv`) with additional `Example`, `Context` columns. Trained 5 epochs with LoRA rank 8.
        - 3rd Attempt: Used advanced dataset. Trained 10 epochs with LoRA rank 8. -> Final Result
    - **HuggingFace:** [HuggingFace Model](https://huggingface.co/SeoyeonPark1223/genz-slang-generator)