# Reasoning Models Better Express Their Confidence

---
## Installation
```
# clone the repository
pip install -e lm-eval-harness
pip install -e evalchemy
pip install vllm
```

## Section 3: Main Experiment

1. For **reasoning models** that reliably generate "Confidence Reasoning":
```
bash evalchemy/scripts/reasoning_no_force.sh
```

2. For **reasoning models** that do not reliably generate "Confidence Reasoning" (R1 Distill, OR1-Preview, GLM Z1):
```
bash evalchemy/scripts/reasoning_force.sh
```

3. For **non-reasoning models**:
```
bash evalchemy/scripts/non_reasoning.sh
```

4. Finally, use the notebook `results/calculate_metrics.ipynb` to calculate ECE, Brier Score, and AUROC for the outputs.

---
## Section 4: Analysis
### Section 4.1: Linear Regression
1. For **reasoning models**:
```
bash evalchemy/reasoning_slope.sh
```

2. For **non-reasoning models**:
```
bash evalchemy/non_reasoning_slope.sh
```

3. Finally, use the notebook `results/linear_regression.ipynb` to run linear regression on the calibration metrics.

**Change the dataset path and the model name appropriately referring to the list below.**

<details>
  <summary>Paths to the segmented CoTs</summary>

  <b>Reasoning Models</b>  
  - datasets/slopes/reasoning/qwen3-think-nonambigqa-slope.jsonl  
  - datasets/slopes/reasoning/qwen3-think-triviaqa-slope.jsonl  
  - datasets/slopes/reasoning/r1-nonambigqa-slope.jsonl  
  - datasets/slopes/reasoning/r1-triviaqa-slope.jsonl  
  - datasets/slopes/reasoning/exaone-deep-nonambigqa-slope.jsonl  
  - datasets/slopes/reasoning/exaone-deep-triviaqa-slope.jsonl  
  - datasets/slopes/reasoning/glm-z1-nonambigqa-slope.jsonl  
  - datasets/slopes/reasoning/glm-z1-triviaqa-slope.jsonl  


  <b>Non-Reasoning Models</b>  
  - datasets/slopes/reasoning/qwen3-non-think-nonambigqa-slope.jsonl  
  - datasets/slopes/reasoning/qwen3-nonthink-triviaqa-slope.jsonl  
  - datasets/slopes/reasoning/glm-instruct-nonambigqa-slope.jsonl  
  - datasets/slopes/reasoning/glm-instruct-triviaqa-slope.jsonl  
  - datasets/slopes/reasoning/exaone-instruct-nonambigqa-slope.jsonl  
  - datasets/slopes/reasoning/exaone-instruct-triviaqa-slope.jsonl  
  - datasets/slopes/reasoning/qwen25-nonambigqa-slope.jsonl  
  - datasets/slopes/reasoning/qwen25-triviaqa-slope.jsonl  
</details>

### Section 4.2: Ablation
```
bash evalchemy/reasoning_ablations.sh
```

The code used to create the ablated CoTs are available in `ablation_data/`.

### Section 4.3: In-context Slow Thinking
```
bash evalchemy/non_reasoning_slow_think.sh
```
The few-shot slow thinking examples are available in `evalchemy/eval/chat_benchmarks/non_reasoning_slow_think/few_shot_prompt.py`

