
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

## 7.1 How Google Search Works

Google Search mainly works in **3 steps**:

```text
🌐 Web
  ↓
1. Crawling
  ↓
2. Indexing
  ↓
3. Ranking
  ↓
🔎 Search Results
```

### 1. 🕷️ Crawling

Google uses automated programs called **Googlebot** to discover and visit web pages.

New pages can be discovered through:

- 🔗 Links from existing pages
    
- 🗺️ Sitemaps
    
- 🔄 Revisiting known pages
    
- 📤 URL submissions through Search Console
    

> Google does **not** simply run one cron job over the entire internet. It uses a large, distributed crawling system that continuously decides **what to crawl and when**.

### 2. 📚 Indexing

Google analyzes the crawled pages and stores information about them in its **Search Index**.

```text
Web Page → Crawl → Analyze → Search Index
```

Google doesn't scan the entire internet every time you search.

### 3. 🏆 Ranking

When you search, Google finds relevant pages from its index and ranks them using many signals such as:

- Relevance
    
- Quality
    
- Freshness
    
- Location/context
    

```text
Your Query
    ↓
Search Index
    ↓
Relevant Pages
    ↓
Ranking
    ↓
Search Results
```

### ⚠️ Important

**Crawling ≠ Indexing**

A page being discovered and crawled **doesn't guarantee** that Google will index it or show it in search results.

### 🔑 Remember

> **Crawling → Discover pages**  
> **Indexing → Store/analyze pages**  
> **Ranking → Order the results**

**Google Search = Retrieve + Rank existing information.**

---

## 7.2 How ChatGPT Works

Unlike Google Search, ChatGPT primarily **generates an answer using an AI model** rather than simply retrieving and ranking web pages.

```text
User Prompt
    ↓
Tokenization
    ↓
LLM / Transformer
    ↓
Predict next tokens
    ↓
Generated Response
```

### 1. 💬 User Prompt

You ask something like:

> "Explain recursion in JavaScript."

Your text is converted into **tokens** that the model can process.

### 2. 🧠 LLM Processes the Prompt

The tokens are passed to the **Large Language Model (LLM)**.

The model has learned patterns from its training data and uses the context of your prompt to determine an appropriate response.

### 3. 🔮 Predicts Tokens

The model generates the response **token by token**, predicting what is most likely to come next.

```text
"Recursion is"
       ↓
"a function"
       ↓
"that calls"
       ↓
"itself..."
```

This happens very quickly, repeatedly, until the response is complete.

### 4. 🤖 Generates the Answer

The final tokens are converted back into readable text and shown to you.

### 🔑 Important Difference

```text
Google Search

Query
 ↓
Search Index
 ↓
Find + Rank existing pages
 ↓
Results


ChatGPT

Prompt
 ↓
LLM
 ↓
Generate tokens
 ↓
Answer
```

> **Google Search → Finds existing information.**  
> **ChatGPT → Generates a response based on patterns learned by its model.**

---

## 8. AI Hallucination

### 🤔 What is Hallucination?

**AI Hallucination** is when an AI generates information that **sounds correct but is actually false, inaccurate, or made up**.

### Example

You ask:

> **"Who invented JavaScript?"**

Correct answer:

> **Brendan Eich**

If AI confidently says:

> "JavaScript was invented by James Gosling in 1995."

That's a **hallucination** — the answer sounds believable but is incorrect.

### Why does it happen?

An LLM generates text by **predicting the next token based on patterns learned during training**. It doesn't automatically verify whether every generated statement is factually correct.

```text
Prompt
  ↓
LLM
  ↓
Predicts likely tokens
  ↓
Generates answer
  ↓
❌ Incorrect / fabricated information
  ↓
Hallucination
```

### 🔑 Remember

> **Hallucination = A confident-sounding AI answer that is factually incorrect or fabricated.**

---

## 9. Why Does AI Hallucination Occur?

### 🧠 Core Reason

An LLM is primarily trained to **predict the next token**, not to automatically verify whether every fact is true.

```text
Prompt
  ↓
LLM
  ↓
Predicts likely next token
  ↓
Generates response
```

If the model doesn't have reliable information, it may still generate an answer that **sounds plausible but is incorrect**.

### Main Reasons

1. **Next-token prediction** → The model's primary objective is to generate plausible text, not verify every fact.
    
2. **Missing or incomplete knowledge** → The required information may not have been present in its training data.
    
3. **Ambiguous questions** → The model may make assumptions when the question is unclear.
    
4. **Conflicting data** → Training data can contain contradictory or incorrect information.
    
5. **No fact verification** → Without external tools such as web search, the model may not be able to independently verify a claim.
    

### 🔑 Remember

> **LLM predicts what is likely to be said, not automatically what is definitely true.**

Therefore, an AI can sometimes produce a **confident-sounding but incorrect answer** — this is called **hallucination**.

---

## 10. How ChatGPT Uses Tools

An **LLM alone** has limitations. It mainly generates text based on patterns learned during training.

ChatGPT can use **external tools** to perform tasks that require additional capabilities.

### 🧠 Basic Flow

```text
User
 ↓
ChatGPT
 ↓
LLM decides:
"Can I answer this directly?"
 ↓
 ┌───────────────┬────────────────┐
 ↓               ↓
Yes              No / Tool needed
 ↓               ↓
Answer       Call a Tool
                 ↓
             Tool Result
                 ↓
              LLM
                 ↓
              Answer
```

### 🔧 Examples of Tools

|Tool|Purpose|
|---|---|
|🌐 **Web Search**|Find current information from the internet|
|🧮 **Calculator**|Perform accurate calculations|
|💻 **Code / Python**|Run code and analyze data|
|📄 **File Tools**|Read and analyze uploaded documents|
|🖼️ **Image Tools**|Understand or generate images|

### Example: Current Information

You ask:

> **"What is Apple's stock price today?"**

The LLM's training data may not contain today's price.

So ChatGPT can:

```text
User Question
     ↓
LLM
     ↓
Needs current information
     ↓
🌐 Web / Market Tool
     ↓
Current Price
     ↓
LLM
     ↓
Final Answer
```

### 🔑 Important

> **The LLM decides when a tool is useful, the tool performs the task, and the LLM uses the result to generate the final response.**

### 🧠 Simple Analogy

Think of the **LLM as the brain** and tools as its **external abilities**.

```text
             🧠 LLM
               │
      ┌────────┼────────┐
      ↓        ↓        ↓
   🌐 Web    🧮 Calc   💻 Code
```

The important distinction is:

> **The tool provides information or performs an operation; the LLM interprets the result and communicates it to you.**

---

