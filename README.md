# RadDiagVQA Dataset
RadDiagVQA is a comprehensive medical imaging Visual Question Answering (VQA) dataset focusing on real-world clinical diagnostic scenarios. The dataset is compiled from six authoritative medical publications and platforms up to May 2024.

The dataset consists of two types of cases:
- Multiple-choice questions (with 4-5 options)
- Short-answer questions (standardized as "What is the diagnosis?")

Each case comprises:
- Clinical history
- Radiological images (1-16 images per case)
- Corresponding diagnostic questions and answers

This dataset aims to facilitate the development and evaluation of multimodal LLM in understanding and reasoning about radiological images in real clinical settings.

## Dataset Structure

The dataset consists of 6 sub-datasets:

### Available Datasets

1. **Lancet-PQ**
   - Source: Picture Quiz in the The Lancet 
   - Format: Multiple-choice questions (four choices)
   - Data format: JSON file (`./json/data_lancet-pq.json`)

2. **NEJM-IC**
   - Source: Image Challenge in the New England Journal of Medicine 
   - Format: Multiple-choice questions (five choices)
   - Data format: JSON file (`./json/data_nejm-ic.json`)
   
3. **Eurorad-TC**
   - Source: Teaching Cases in Eurorad 
   - Format: Short-answer questions
   - Data format: JSON file (`./json/data_eurorad-tc.json`)

4. **X-CookyJar**
   - Source: Cases From the Cooky Jar on X (formerly Twitter)
   - Format: Short-answer questions
   - Data format: JSON file (`./json/data_x-cookyjar.json`)

    
### Download-Only Datasets (Due to Copyright Restrictions)

5. **JAMA-CCR**
   - Source: Clinical Challenge in JAMA Learning
   - Format: Multiple-choice questions (four choices)
   - Access: Download links provided in `./json/data_jama-ccr_downloadlink.json`
   - 
6. **Radiology-DP**
   - Source: Diagnosis Please in Radiology 
   - Format: Short-answer questions
   - Access: Download links provided in `./json/data_radiology-dp_downloadlink.json`



## Data Format

### Multiple-choice Format
```json
{
    "ID": "unique_identifier",
    "DataSource": "source_name",
    "Subspecialty": "medical_subspecialty",
    "Modality": "imaging_modality",
    "Link": "source_link",
    "Type": "question_type",
    "Question": "question_text",
    "OptionA": "option_a_text",
    "OptionB": "option_b_text",
    "OptionC": "option_c_text",
    "OptionD": "option_d_text", 
    "OptionE": "option_e_text", 
    "Answer": "correct_answer_text",
    "AnswerLabel": "correct_option_label",
    "num_image": "number_of_images",
    "image_ids": ["list_of_image_filenames"]
}
```

### Short-answer Format
```json
{
    "ID": "unique_identifier",
    "DataSource": "source_name",
    "Subspecialty": "medical_subspecialty",
    "Modality": "imaging_modality",
    "Link": "source_link",
    "Type": "question_type",
    "Question": "question_text",
    "Answer": "answer_text",
    "num_image": "number_of_images",
    "image_ids": ["list_of_image_filenames"]
}
```


### Directory Structure
 ```
RadDiagVQA/
├── images/
│ ├── Eurorad-TC/
│ ├── X-CookyJar/
│ ├── Lancet-PQ/
│ └── NEJM-IC/
└── jsons/
├── data_eurorad-tc.json
├── data_x-cookyjar.json
├── data_lancet-pq.json
├── data_nejm-ic.json
├── data_radiology-dp_downloadlink.json
└── data_jama-ccr_downloadlink.json
 ```

## Usage
To load and use the dataset:
```python
import json

# Load any dataset
with open('data_eurorad-tc.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# Access data
for item in data:
    print(item['Question'])
    print(item['Answer'])
    print(item['image_ids'])
```

## Citation
If you find this dataset useful in your research, please cite our paper:
```tex
@article{raddiagvqa2024,
  title={Benchmarking multimodal large language models against human expertise in radiology},
  author={Qingxia Wu, Qingxia Wu, Peipei Zhang et al.},
  journal={arXiv preprint},
  year={2025}
}