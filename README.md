# RadDiagVQA Dataset
RadDiagVQA is a comprehensive medical imaging Visual Question Answering (VQA) dataset containing radiology images and their corresponding questions and answers. 
The dataset is compiled from various medical sources and includes both short-answer and multiple-choice questions.

## Dataset Structure

The dataset consists of 6 sub-datasets:

### Available Datasets

1. **Lancet-PQ**
   - Source: Picture Quiz in the The Lancet 
   - Format: Multiple-choice questions
   - Data format: JSON file (`./json/data_lancet-pq.json`)

2. **NEJM-IC**
   - Source: Image Challenge in the New England Journal of Medicine 
   - Format: Multiple-choice questions
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

5. **Radiology-DP**
   - Source: Diagnosis Please in Radiology 
   - Format: Short-answer questions
   - Access: Download links provided in `./json/data_radiology-dp_downloadlink.json`

6. **JAMA-CCR**
   - Source: Clinical Challenge in JAMA Learning
   - Format: Multiple-choice questions
   - Access: Download links provided in `./json/data_jama-ccr_downloadlink.json`

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
    "OptionE": "option_e_text", # Only available in NEJM-IC dataset
    "Answer": "correct_answer_text",
    "AnswerLabel": "correct_option_label",
    "num_image": number_of_images,
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
    "num_image": number_of_images,
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

