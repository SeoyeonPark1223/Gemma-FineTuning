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
    - **HuggingFace:** [HuggingFace Model](https://huggingface.co/SeoyeonPark1223/genz-slang-generator)

- **Model Training**
    1. **1st Attempt:**
        - The initial attempt involved a smaller dataset of approximately 150 rows, which included only two columns: Slang and Description. This simplified dataset was intended to give the model a basic understanding of popular GenZ slang and their corresponding meanings. 
        - To minimize resource usage, the model was trained for just 1 epoch, and a LoRA (Low-Rank Adaptation) rank of 4 was applied. This setup provided an initial, but limited, baseline for how the slang generator might perform, but the lack of contextual and example-based training limited the depth of the generated output.
	2. **2nd Attempt:**
        - For the second round of tuning, a more comprehensive dataset, all_slangs.csv, was utilized. This dataset expanded the available information by adding Example and Context columns, providing the model not only with the slang definitions but also practical usage scenarios and conversational contexts. 
        - The model was trained for 5 epochs with a LoRA rank of 8, allowing the generator to build a more nuanced understanding of how slang terms fit within different conversation flows and contexts. This tuning significantly improved the model’s ability to generate context-aware slang, although some variability in accuracy was observed.
	3. **3rd Attempt (Final Result)**:
        - In the final tuning attempt, the advanced dataset ( [all_slangs.csv](https://huggingface.co/datasets/SeoyeonPark1223/genz-slangs)) was once again employed, but this time the training process was extended to 10 epochs with the LoRA rank still set to 8. This longer training session allowed the model to better capture the intricate relationships between slang, their descriptions, and how they are used in various contexts. The result was a slang generator that not only understood GenZ terms but also could generate them in contextually appropriate and creative ways. This step achieved the final desired outcome for the project.

- **Example Usage:**
    1. Initial Setup
        - To start generating slang terms, define a tag that outlines the instructions for the model:

        ```python
        tag = (
            "Given the context below, create a new slang term. "
            "The slang should be catchy, easy to use, and relevant to modern youth culture. "
            "Make sure it's something that would feel natural in casual conversation:\n\n"
        )
        ```
    2. Define Specific Context
        - Set the context for the slang generation. For example:
        ```python
        context = "You're hanging out with friends at a new restaurant, trying out some unique fusion dishes."
        ```

    3. Define Conditions
        - Specify additional conditions for the output. For example, you can request the definition and examples:
        ```python
        condition = "You should suggest new slang and its definition, also give an example for clarification. Example should be long and also precise."
        ```

    4. Final Prompt Construction
        - Construct the final prompt by combining the tag, context, and condition:
        ```python
        prompt = template.format(
            instruction=tag + context + condition,
            response=""
        )
        ```

- **Conclusion:**
    - With this slang generator, you can easily create new and engaging slang terms tailored to various contexts. Feel free to modify the context and conditions to explore different slang outputs!
    - LinkedIn Post: [LinkedIn Post](https://www.linkedin.com/posts/seoyeon-park-tris1223_mlbtriogenz-slang-generator-hugging-face-activity-7247268688586764288-Vl87?utm_source=share&utm_medium=member_desktop)
