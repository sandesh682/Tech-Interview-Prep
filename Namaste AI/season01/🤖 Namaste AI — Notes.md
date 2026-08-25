
## 1. What is AI?

### Definition

**Artificial Intelligence (AI)** is the field of creating machines/software that can perform tasks that normally require **human intelligence**.

Examples:

- 🧠 Learning
    
- 🔍 Pattern recognition
    
- 🗣️ Understanding language
    
- 🤔 Reasoning
    
- 🎯 Decision making
    

### Why "Artificial"?

**Artificial ≠ Fake**

Artificial means **created by humans**.

- **Natural Intelligence** → Intelligence naturally present in humans/animals.
    
- **Artificial Intelligence** → Intelligence-like capabilities created in machines.
    

### Simple Example

```text
Human
  ↓
Sees an image
  ↓
Recognizes → "Cat"

AI
  ↓
Receives an image
  ↓
Recognizes → "Cat"
```

The AI's ability is **artificially created**, hence **Artificial Intelligence**.

### 🔑 Key Takeaway

> **AI = Human-created systems that can perform tasks requiring intelligence.**

**Remember:**

`Artificial` → Human-created  
`Intelligence` → Ability to learn, reason, recognize, decide, etc.

---

## 2. History / Evolution of AI

| Year            | Milestone                    | What happened?                                                                                                                                                                                                                                      |
| --------------- | ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1950**        | 🧪 **Turing Test**           | Alan Turing proposed a test to evaluate whether a machine can exhibit human-like intelligence.                                                                                                                                                      |
| **1955**        | 🤖 **Term "AI"**             | John McCarthy and colleagues introduced the term **Artificial Intelligence**.                                                                                                                                                                       |
| **1956**        | 🏛️ **Dartmouth Conference** | AI became established as a formal field of research.                                                                                                                                                                                                |
| **1960s–70s**   | 🧠 **Early AI**              | Focused on logic, rules, search and problem-solving.                                                                                                                                                                                                |
| **1980s**       | 👨‍⚕️ **Expert Systems**     | AI systems used human-written rules and expert knowledge to make decisions.                                                                                                                                                                         |
| **1970s–80s**   | ❄️ **AI Winter**             | AI funding and interest declined because early systems failed to meet expectations.                                                                                                                                                                 |
| **1990s**       | 📊 **Machine Learning**      | AI increasingly shifted from manually written rules to **learning patterns from data**.                                                                                                                                                             |
| **1990s–2000s** | 👁️ **Computer Vision**      | A field of AI focused on enabling computers to **understand images and videos**. Examples include face recognition, object detection and image classification.                                                                                      |
| **1990s–2000s** | 💬 **NLP**                   | **Natural Language Processing** focuses on enabling computers to understand, process and generate **human language**. Examples include translation, speech recognition and text analysis.                                                           |
| **2000s–2010s** | 🧠 **Deep Learning**         | A type of Machine Learning based on **multi-layered neural networks**. Large datasets, GPUs and better algorithms made Deep Learning extremely powerful for tasks such as Computer Vision and NLP.                                                  |
| **2012**        | 🚀 **AlexNet**               | A major Deep Learning breakthrough in image recognition that demonstrated the power of deep neural networks.                                                                                                                                        |
| **2017**        | ⚡ **Transformers**           | The paper _Attention Is All You Need_ introduced the **Transformer architecture**. Its key idea, **self-attention**, allows the model to understand relationships between different parts of a sequence and enabled efficient large-scale training. |
| **2018+**       | 🧠 **LLMs**                  | **Large Language Models** are very large neural networks, typically based on Transformers, trained on huge amounts of text. They can understand and generate human-like language and perform many tasks using natural language.                     |
| **2020s**       | ✨ **Generative AI**          | AI evolved toward generating new content such as **text, images, audio, video and code**.                                                                                                                                                           |
| **2022**        | 💬 **ChatGPT**               | ChatGPT brought LLMs and Generative AI into mainstream public use.                                                                                                                                                                                  |

---

## 3. Machine Learning vs Deep Learning

### 🐱 Same Problem: Identify Whether an Image Is a Cat

|**Machine Learning**|**Deep Learning**|
|---|---|
|**Goal:** Identify whether an image contains a cat.|**Goal:** Identify whether an image contains a cat.|
|**1. Collect images** → Thousands of cat and non-cat images.|**1. Collect images** → Thousands of cat and non-cat images.|
|**2. Humans identify features** → We decide what the model should look at: **ears, eyes, fur, color, shape, edges**, etc.|**2. Give images directly to the neural network** → We don't manually define the important features.|
|**3. Extract features** → Convert each image into these selected features.|**3. Neural network processes the image** through multiple layers.|
|**4. Train ML algorithm** using the extracted features.|**4. Layers automatically learn features** from the images.|
|**5. Model learns** → It learns patterns such as _pointed ears + fur + certain shapes → probably a cat_.|**5. Layers learn progressively** → **Edges → shapes → eyes/ears → face/body → cat**.|
|**6. Give a new image** → Extract the same predefined features.|**6. Give a new image** → The trained network processes it directly.|
|**7. Prediction** → `CAT 🐱`|**7. Prediction** → `CAT 🐱`|
|**Key idea:** Humans decide **what features are important**.|**Key idea:** The neural network **learns what features are important**.|

---

## 4. How are LLMs Trained?

**LLM = Large Language Model**

An LLM is trained on a **huge amount of text data** so that it can learn patterns in language and predict what comes next.

### 🧠 Basic Training Process

```text
Huge Amount of Text
        ↓
Data Cleaning & Preparation
        ↓
Tokenization
        ↓
Training the Neural Network
        ↓
Learn Patterns & Relationships
        ↓
Trained LLM
```

### 1. 📚 Collect Data

The model is trained using massive amounts of text from sources such as:

- Books
    
- Websites
    
- Articles
    
- Documents
    
- Code
    
- Other text datasets
    

The goal is to expose the model to a wide variety of language patterns.

### 2. 🔤 Tokenization

Text is converted into **tokens** that the model can process.

Example:

```text
"I love programming"

        ↓

["I", "love", "program", "ming"]
```

A token can be a whole word, part of a word, punctuation, etc.

### 3. 🧠 Training

The model is given text and learns to **predict the next token**.

Example:

```text
"The sky is"

       ↓

Model predicts:

"blue"
```

If the prediction is wrong, the model calculates how wrong it was and adjusts its internal parameters.

This process is repeated **billions/trillions of times**.

```text
Input → Prediction → Error → Adjust Parameters
                    ↑             ↓
                    └─────────────┘
                         Repeat
```

### 4. 🔄 What Does the Model Actually Learn?

It doesn't simply memorize a dictionary.

Through training, it learns statistical patterns and relationships such as:

- Grammar
    
- Vocabulary
    
- Sentence structure
    
- Relationships between words
    
- Context
    
- Facts and patterns present in the training data
    
- Code patterns
    
- Different styles of language
    

### 5. 🏋️ Pre-training

The large-scale process described above is called **pre-training**.

The result is a **base model** that has learned general patterns of language.

```text
Massive Text Dataset
        ↓
    Pre-training
        ↓
    Base LLM
```

### 6. 🎯 Fine-tuning / Alignment

After pre-training, the model can be further trained to become better at following instructions and interacting with users.

```text
Base LLM
   ↓
Fine-tuning / Alignment
   ↓
Instruction-following LLM
```

This is why a chatbot can respond to:

> "Explain recursion in JavaScript"

rather than simply continuing the sentence.

---

### 🔑 Golden Rule

> **LLM training is primarily about learning patterns from huge amounts of data by repeatedly predicting tokens and adjusting the model's parameters when its predictions are wrong.**

### 🧠 Remember

```text
Data
 ↓
Tokenization
 ↓
Predict next token
 ↓
Calculate error
 ↓
Adjust parameters
 ↓
Repeat billions/trillions of times
 ↓
Trained LLM
```

---

## 5. Knowledge Cutoff Date

### What is a Knowledge Cutoff?

A **knowledge cutoff date** is the date up to which information was generally included in an AI model's training data.

```text
Training Data
      ↓
Data available up to cutoff
      ↓
     LLM
```

### Example

If an LLM has a knowledge cutoff of **January 2024**:

```text
Information before Jan 2024
        ↓
   Model may know it

Information after Jan 2024
        ↓
 Model may not know it reliably
```

### 🔑 Important

> **Knowledge cutoff ≠ Ability to access current information**

An LLM can have a fixed training cutoff but still access **up-to-date information** through external tools such as web search or APIs.

### 🧠 Remember

**Training Data → Knowledge Cutoff → Model Knowledge**

> The cutoff tells us roughly **how recent the information in the model's training data is**, not necessarily what information the model can access right now.

---

## 6. Base Models & Fine-Tuning

### 🧠 Base Model

A **Base Model** is an LLM after pre-training on a massive amount of data.

It learns:

- Language and grammar
    
- Patterns and relationships
    
- General knowledge
    
- Code and other information
    

```text
Massive Data
    ↓
Pre-training
    ↓
Base Model
```

### 🎯 Fine-Tuning / Alignment

After pre-training, the model can be further trained to **follow instructions and behave according to desired rules and safety guidelines**.

### Example

A base model may have encountered information about **movie piracy** during training.

If a user asks:

> "How can I pirate movies?"

A deployed, aligned model can be trained to **refuse to provide instructions that facilitate piracy**, even though related information may exist in its underlying knowledge.

```text
Base Model
    ↓
Fine-Tuning / Alignment
    ↓
Instruction-following + Safety
    ↓
Final AI Model
```

### 🔑 Remember

> **Pre-training → learns knowledge and patterns.**

> **Fine-tuning / Alignment → teaches the model how to respond and follow desired instructions and safety rules.**

---

