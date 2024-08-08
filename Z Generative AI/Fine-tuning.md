In context learning
- May not work for smaller models
- Examples take up space in the context window
	- reduce the amount of room to include useful information


First steep of fin tuning: Prepare the data

### Single task fine tuning
Fine tuning on a single task may not require that much data, but it will cause catastrophic forgetting.
Catastrophic forgetting: When fine tuning a model on specific one task, it may start forgetting other task
- Avoid catastrophic forget:
	1. Might not have to
	2. do multiple tasks
	3. Consider parameter efficient fine-tuning(PEFT)

### Multi-task fine-tuning
- It avoid catastrophic forgetting
- Learn to be good at many at the same time
- draw back; REQUIRES A LOT OF data

- Flan (Fine-tuning Language net): specific set of instructions used to perform instruction fine-tuning

![[Pasted image 20240806154718.png]]![[Pasted image 20240806161736.png]]
Model Evaluation:
ROUGE:
- Used for text summarization
- Compare a summary to one or more reference summaries
-
![[Pasted image 20240806162343.png]]
![[Pasted image 20240806162438.png]]
![[Pasted image 20240806162608.png]]
BLEU SCORE
- Use for text translation\
- compare to human-generated translations
unigram: 1 word
bigram: 2 word
n-gram: n words

### LLMs Evaluation benchmarks

GLUE:
SuperGLUE
HELM:
- Metrics
	1. Accuracy
	2. Calibration
	3. Robustness
	4. Fairness
	5. Bias
	6. Toxicity
	7. Efficiency


