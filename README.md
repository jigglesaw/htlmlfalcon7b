# Html_builder using fine-tuned falcon7b model

This project leverages the falcon7b LLM model, fine-tuned to serve as a website-building assistant. The primary technologies employed include Hugging Face Transformers and a dataset originally containing HTML and label data, later adjusted to align with the prompt template.

## Quantization and Training

The 15GB LLM model has undergone 4-bit quantization for efficient single-GPU operation. Utilizing Parameter Efficient Fine Tuning (PEFT) and the Low-Rank Adaptation Config (LORA), the project adopts a modular approach, optimizing resource usage for transfer learning. Customizable parameters accommodate specific requirements. The training process involves evaluating the training loss and stopping at one epoch due to time constraints.

## Merging the saved pretrained model with tokenizer

Combining the base model and the newly fine-tuned model results in a cohesive model, accessible [here](https://huggingface.co/jigglesaw/Finetuned_htmlmaker).

## Evaluation and API Generation

Assessing model accuracy encounters challenges due to limited compute units. The dataset can be split into training and testing subsets, and with the trained model, accuracy can be evaluated using a simple call after logging in through Hugging Face. The provided Flask API serves the model, accepting JSON input with the format `{"prompt": "Write an HTML code to create a login page"}`.

## Errors and problems faced

The main error was the lack of computing power due to the lack of a good gpu for my local system. Thus had to rely on the t4 gpu provided by google collab. This had limits and was always finishing and crashing everytime I tried to train the model. All units were finished by the time one epoch was completed. Accuracy calculation couldn't be done at the time due to the run time reloading everytime the model was loaded. 

## Merits

Was able to save the trained model and merge it with the base model and pushed it to Hugging Face: https://huggingface.co/jigglesaw/Finetuned_htmlmaker
