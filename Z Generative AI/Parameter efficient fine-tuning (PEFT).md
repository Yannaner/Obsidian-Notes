Full fine tuning challenges:
- Temp memory
- Forward activation
- Gradients
- Optimizer states
- Trainable weights

PEFT methods:
Selective:
- Select subset of initial LLM parameters to fine-tune
Reparameterization:
- weights using  a low rank representation
- LoRA method(Low rank adaptation of large language models)
	- 
Additive:
- Add trainable layers or parameters to model
	- Adapter
	- Soft Prompts
		- Prompt Tuning