---
license: apache-2.0
datasets:
- asset
- wi_locness
- GEM/wiki_auto_asset_turk
- discofuse
- zaemyung/IteraTeR_plus
language:
- en
metrics:
- sari
- bleu
- accuracy
---
# Model Card for CoEdIT-Large

This model was obtained by fine-tuning the corresponding google/flan-t5-large model on the CoEdIT dataset. Details of the dataset can be found in our paper and repository.

Paper: CoEdIT: ext Editing by Task-Specific Instruction Tuning
Authors: Vipul Raheja, Dhruv Kumar, Ryan Koo, Dongyeop Kang

## Model Details

### Model Description

- **Language(s) (NLP)**: English
- **Finetuned from model:** google/flan-t5-large

### Model Sources [optional]

- **Repository:** https://github.com/vipulraheja/coedit
- **Paper [optional]:** [More Information Needed]

## How to use
We make available the models presented in our paper. 

<table>
  <tr>
    <th>Model</th>
    <th>Number of parameters</th>
  </tr>
  <tr>
    <td>CoEdIT-large</td>
    <td>770M</td>
  </tr>
  <tr>
    <td>CoEdIT-xl</td>
    <td>3B</td>
  </tr>
  <tr>
    <td>CoEdIT-xxl</td>
    <td>11B</td>
  </tr>  
</table>


## Uses

## Text Revision Task
Given an edit instruction and an original text, our model can generate the edited version of the text.<br>

![task_specs](https://huggingface.co/grammarly/coedit-xl/resolve/main/Screen%20Shot%202023-05-12%20at%203.36.37%20PM.png)

## Usage
```python
from transformers import AutoTokenizer, T5ForConditionalGeneration

tokenizer = AutoTokenizer.from_pretrained("grammarly/coedit-large")
model = T5ForConditionalGeneration.from_pretrained("grammarly/coedit-large")
input_text = 'Fix grammatical errors in this sentence: New kinds of vehicles will be invented with new technology than today.'
input_ids = tokenizer(input_text, return_tensors="pt").input_ids
outputs = model.generate(input_ids, max_length=256)
edited_text = tokenizer.decode(outputs[0], skip_special_tokens=True)[0]
```


#### Software
https://github.com/vipulraheja/coedit

## Citation

**BibTeX:**

[More Information Needed]

**APA:**

[More Information Needed]