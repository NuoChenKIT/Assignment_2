# Stretch Task: Reduced vs. Original GPT-2

## 1. Experiment Setup
I created a "Reduced" version of GPT-2 by surgically removing the last Transformer block (Layer 12), reducing `n_layer` from 12 to 11. Both models were fine-tuned on the same BMW corpus for 5 epochs.


## 2. Comparison
| Metric 	            | Original Model 12 Layers | Reduced Model 11 Layers   |
| **Training Time**   | 05:32 min 		           | 05:12 min 		             |
| **Training Loss**   | 2.3707 			             | 2.6907                    |
| **Validation Loss** | 2.8267 			             | 3.1654                    |
| **Perplexity**      | 19.57 			             | 28.03                     |
| **Q&A Accuracy**    | 60%                      | 40%                       |


## 3. Qualitative Observation
**Original Model**: Generated text tends to be more coherent and grammatically correct. Additionally, better ability to integrate contextual information than the reduced model. However, issues with summarizing information persist.

**Reduced Model**: Still understands the topic (BMW), but logical errors still occur. Additionally, the ability to summarize and synthesize information is weak; sometimes the response content does not align with the question's direction, and kontextual comprehension can be lacking.


## 4. Discussion & Trade-offs
**Model Size vs. Quality**: Removing one transformer layer reduced the model size by approximately 7 million parameters (about 5.7% of the total size). Theoretically, this should reduce training memory usage and increase inference speed.
The quality drop is noticeable. The output quality drop is noticeable. This indicates that for specific domains like BMW news release, every layer is important to ensuring text generation capabilities of LLMs.

**Training Speed**: The reduced model trained faster. In a large-scale training environment, reducing layers can significantly save GPU/CPU costs and latency.


## 5. Future Work
If I had more time, I would:
I. Increase model size (number of parameters).
II. Increase the amount of training data.
III. Increase training steps (longer training sessions, larger batch sizes, higher token count training limits).
IV. Using and comparing different tokenizers, a better tokenizer can significantly reduce training difficulty and improve quality.
V. Delve deeper into and optimize the model architecture, incorporating additional network structures.
VI. Use knowledge distillation: Instead of just deleting a layer, I would use the 12-layer model as a "Teacher" to train the 11-layer "Student", which usually yields better results than simple pruning.
VII. Experiment with quantization (8-bit or 4-bit) to reduce size without removing layers.
