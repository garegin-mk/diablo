# Diablo 

Project Plan: Fine-tuning Models for Specific Tasks

## Goal:
The goal of this project is to fine-tune a large language model (LLM) for specific NLP tasks like Question Answering (Q/A), Summarization, and Named Entity Recognition (NER) using a variety of input files (PDF, MD, Word, SharePoint, etc.).

## Tools & Libraries:
- **GPT-based models**: For generating Q/A, summaries, and fine-tuning for task-specific objectives.
- **[MegaParse Library](https://github.com/QuivrHQ/MegaParse/tree/main)**: To parse input files more accurately and convert them into structured data.
  
## Key Steps

### 1. **Parse Input Files and Convert to Markdown (MD)**
- Use **MegaParse** or other parsing libraries to convert input files like PDF, MD, Word, SharePoint into Markdown files.
- Ensure accurate parsing to avoid missing important sections or misinterpreting formatting.
  
### 2. **Dataset Generation**
   - **Subtasks**:
     - Extract meaningful content from parsed files.
     - Generate task-specific datasets (e.g., Q/A pairs, entity extraction examples, summaries).
     - Use existing models to auto-generate initial datasets or manually curate some data for fine-tuning.
     - Clean and format the dataset for training.
  
   - **Approach**:
     - Use GPT models to create Q/A pairs based on the parsed text.
     - Summarization and named entity extraction datasets can be auto-generated from the text.
     - Ensure dataset quality through a validation step, avoiding hallucinations and incorrect information.
   
### 3. **Prompt Template Creation**
   - **Purpose**: Define task-specific templates for Q/A, NER, and Summarization prompts to standardize the input for the model.
   
   - **Templates**:
     - **Q/A Template**: Structure the input as a context + question pair, focusing on retrieving factual answers.
       - **Example**: 
         - **Context**: `[Document Text]`
         - **Question**: `[Generated or user-defined question]`
         - **Answer**: `[Model’s predicted answer]`
     - **NER Template**: Create input/output pairs where entities are extracted from the given text.
       - **Example**: 
         - **Text**: `[Input Text]`
         - **Entities**: `[Entity1: Value, Entity2: Value...]`
     - **Summarization Template**: Concise, coherent summaries of large texts.
       - **Example**:
         - **Original Text**: `[Full document or section]`
         - **Summary**: `[Summarized text]`
     
   - **Goal**: Avoid hallucinations in the output by carefully guiding the model via task-specific templates.

### 4. **Fine-Tuning the Model**
   - Fine-tune GPT or other LLMs using the dataset created from parsed files.
   - Fine-tune the model for each task (Q/A, Summarization, NER) separately.
     - **Training**:
       - Feed task-specific datasets into the model.
       - Train until performance metrics (accuracy, precision, recall) improve satisfactorily.
     - Evaluate the model on different inputs and test for overfitting.
  
### 5. **Testing and Validation**
   - Validate the model by testing it on unseen documents.
   - Ensure the model provides accurate Q/A answers, extracts entities correctly, and generates coherent summaries.
  
## Final Output:
- A fine-tuned language model capable of performing specific tasks (Q/A, Summarization, NER) with high accuracy on documents of various formats.
