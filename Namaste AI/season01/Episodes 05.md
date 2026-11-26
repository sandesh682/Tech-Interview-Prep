## Q1. From Text to Embeddings

LLMs ultimately work with **numbers**, so text goes through these stages:

```text
"I love AI"
    ↓
Tokenization
    ↓
["I", " love", " AI"]
    ↓
Token IDs
    ↓
[40, 1842, 955]
    ↓
Embedding Vectors
```

### 🧠 What happens?

|Stage|What it does|
|---|---|
|**Tokenization**|Text → Tokens|
|**Token ID**|Token → Unique number|
|**Embedding**|Token ID → Learned numerical vector|

### What is an Embedding?

Token IDs are just **identifiers**. The number `40` itself has no meaning. **For a given model each Token ID points to a learned vector.**
 
**Embedding** is a way to represent something such as a word, sentence, image or audio clip as a list of numbers (a vector) so an AI system can compare it mathematically.

```text
cat → [0.21, 0.73, -0.12, ...]
dog → [0.19, 0.70, -0.10, ...]
car → [-0.81, 0.12, 0.65, ...]
```

`cat` and `dog` can have more similar representations because they are semantically related.

### 🔑 Remember

> **Token = piece of text**  
> **Token ID = identifier**  
> **Embedding = learned vector representation**

> **Vectorization is the general concept of converting data into numerical vectors; an embedding is a learned vector representation.**

---

## Q2. Embeddings as Coordinates

Think of an **embedding vector as coordinates in a mathematical space**.

Just like a location can be represented as:

```text
Point A = (2, 3)
Point B = (2.5, 3.2)
Point C = (9, 1)
```

an embedding represents a token using many numerical coordinates:

```text
cat → [0.21, 0.73, -0.12, 0.45, ...]
dog → [0.19, 0.70, -0.10, 0.41, ...]
car → [-0.81, 0.12, 0.65, 0.02, ...]
```

These coordinates define **where the token sits in the embedding space**.

### 🧠 Why is this useful?

Tokens with related meanings can end up **closer together** in this space.

```text
             dog
            /
       cat
       
                         car
```

So we can think:

> **Embedding = coordinates representing a concept in a high-dimensional space.**

### ⚠️ Important

The dimensions are **not usually human-readable** like:

```text
X = animalness
Y = size
Z = color
```

Instead, the model **learns the numerical dimensions automatically** during training.

### 🔑 Remember

> **Token ID tells us WHICH token it is.**

> **Embedding tells us WHERE that token is represented in the learned vector space.**

---

## Q3. Dimensions in Embeddings

A **dimension** is one numerical value (coordinate) in an embedding vector.

For example, a **4-dimensional embedding** might look like:

```text
cat → [0.21, 0.73, -0.12, 0.45]
       ↑     ↑      ↑      ↑
      D1    D2     D3     D4
```

So:

> **4 dimensions = 4 numbers in the vector.**

### 🧠 Why so many dimensions?

Real-world concepts are complex. A model needs many numerical dimensions to represent the **patterns and relationships** it learns.

For example:

```text
cat → [0.21, 0.73, -0.12, ...]
dog → [0.19, 0.70, -0.10, ...]
```

With hundreds or thousands of dimensions, the model can represent much richer relationships than a simple 2D/3D coordinate system.

### ⚠️ Important

Don't assume:

```text
D1 = animal
D2 = size
D3 = color
```

The dimensions generally **don't have individually understandable meanings**. The meaning is encoded across the **combination of many dimensions**.

### 🔑 Remember

> **Dimension = one coordinate/value in an embedding vector.**

> **Embedding dimension = number of values in the vector.**

```text
Embedding Dimension = Vector Length
```

---

## Q4. What is Semantic Similarity?

**Semantic similarity** means how similar two pieces of text are based on their **meaning**, rather than just the exact words they contain.

### 🧠 Example

```text
"I love dogs"
"I really like puppies"
```

The words are different, but their **meaning is similar**.

Their embeddings may therefore be close in vector space:

```text
        "I love dogs"
             ●
            /
           /
          ●
"I really like puppies"
```

Whereas:

```text
"I love dogs"     ●


                         ●
                    "The car is fast"
```

would likely have lower semantic similarity.

### 📐 How is it measured?

A common method is **Cosine Similarity**.

It compares the direction of two embedding vectors:

```text
Embedding A
     ↘
      \  angle
       \
        ↘ Embedding B

Smaller angle → More similar
Larger angle  → Less similar
```

### 🔑 Remember

> **Semantic similarity = similarity in meaning.**

> **Embeddings allow us to represent meaning numerically, so mathematical similarity can be calculated between texts.**

---

## Q5. How Do Embeddings Capture Relationships?

Embeddings capture relationships because their values are **learned during training from how tokens appear in different contexts**.

### 🧠 Example

Consider the training sentences:

```text
"The cat drinks milk."
"The dog drinks milk."
"The cat eats food."
"The dog eats food."
```

The model repeatedly sees **cat** and **dog** appearing in similar contexts.

During training, their embedding values are adjusted so that they develop **similar representations**.

```text
             Animals
            /       \
         cat         dog
```

But:

```text
             Animals
            /       \
         cat         dog


                         car
                          |
                       Vehicle
```

`cat` and `dog` tend to have more similar representations than `cat` and `car`.

### 🔄 How does learning happen?

```text
Training Data
     ↓
Tokens appear in contexts
     ↓
Model makes predictions
     ↓
Prediction error
     ↓
Model adjusts parameters
     ↓
Repeat billions of times
     ↓
Learned Embeddings
```

Over many examples, the model learns that certain tokens consistently occur in **similar or related contexts**.

### ⚠️ Important

The model does **not** explicitly store:

```text
cat = animal
dog = animal
```

Instead, these relationships emerge from the **patterns learned across many dimensions** of the embedding space.

### 🔑 Remember

> **Relationships are learned from context and repeated patterns in training data.**

> **Similar contexts → embeddings tend to develop related representations.**

---

## Token, Sentence, Paragraph & Media Embeddings

An **embedding** can represent different levels of information depending on the model and use case.

|Type|Represents|Example|
|---|---|---|
|**Token Embedding**|A token|`cat`|
|**Sentence Embedding**|Meaning of a sentence|`"The cat is sleeping."`|
|**Paragraph / Document Embedding**|Meaning of larger text|An article or document|
|**Media Embedding**|Meaning/features of media|Image, audio, video|

### 🧠 Think of it as different levels

```text
Token
  ↓
"cat"
  ↓
Token Embedding

Sentence
  ↓
"The cat is sleeping."
  ↓
Sentence Embedding

Paragraph
  ↓
Several related sentences
  ↓
Paragraph / Document Embedding

Image / Audio / Video
  ↓
Media Embedding
```

### 🔑 Key Idea

> **Embedding = numerical representation of information.**

The important difference is **what information the vector represents**:

```text
Token      → token meaning/representation
Sentence   → sentence meaning
Paragraph  → broader text meaning
Media      → content/features of media
```

The exact way these embeddings are created depends on the **model and architecture**.

---

## 6. Token, Sentence, Paragraph & Media Embeddings

An **embedding** can represent information at different levels.

### 🧠 Token Embedding

For one token, we get **one vector**:

```text
"cat"
  ↓
[0.21, 0.73, -0.12, ...]
```

### 🧠 Sentence Embedding

A sentence contains **multiple tokens**, so internally there can be **multiple token embeddings**.

```text
"I love cats"
     ↓
"I"     → [ ... ]
"love"  → [ ... ]
"cats"  → [ ... ]
     ↓
Combined / represented
     ↓
[0.31, 0.62, -0.14, ...]
        ↑
 One sentence embedding
```

The **sentence embedding is a single vector representing the overall meaning of the sentence**. It is not simply one of the token vectors.

### 🧠 Paragraph / Document Embedding

The same idea can be applied to larger text:

```text
Many tokens
    ↓
Token representations
    ↓
Overall representation
    ↓
One paragraph/document embedding
```

So even a **100-word paragraph** can have **one vector** representing its overall semantic meaning.

### 🖼️ Media Embeddings

The same concept can be applied to media:

```text
Image / Audio / Video
        ↓
Embedding Model
        ↓
Vector representation
```

The exact representation depends on the model.

### 🔑 Remember

|Level|Representation|
|---|---|
|**Token**|One vector per token|
|**Sentence**|Multiple token vectors → one sentence embedding|
|**Paragraph / Document**|Multiple token vectors → one overall embedding|
|**Media**|Content → vector representation|

> **Many token vectors can be used to create a single higher-level embedding representing the overall meaning.**

**Important:** Token embeddings and sentence/document embeddings are **different representations for different purposes**.

---

## 7. How Do Position and Order of Tokens Affect Embeddings?

**Order matters because the same tokens can have different meanings when their positions change.**

### 🧠 Example

```text
"Dog bites man"
"Man bites dog"
```

Both sentences contain the same words, but their meanings are completely different.

```text
Dog → bites → man
 ↑              ↑
subject       object

Man → bites → dog
 ↑              ↑
subject       object
```

Therefore, the model needs to know **where each token appears**.

### 📍 Positional Information

The model adds information about a token's **position/order** along with its token representation.

```text
Token representation
        +
Position information
        ↓
Position-aware representation
```

So:

```text
"Dog" at position 1
        ≠
"Dog" at position 3
```

The same token can therefore contribute differently depending on its **position and surrounding tokens**.

### 🔑 Remember

> **Token identity tells the model WHAT the token is.**

> **Position tells the model WHERE the token is.**

> **Together with context, this allows the model to understand the order and relationships between tokens.**

---

## 8. Static vs Contextual Meaning (Contextualization)

A word can have a **fixed representation** or a **context-dependent representation**.

### 1️⃣ Static Meaning

A word has **one fixed vector**, regardless of where it appears.

```text
"bank" → [0.21, 0.73, -0.12, ...]
```

So:

```text
"I deposited money in the bank."
"The river bank is beautiful."
```

Both occurrences of **bank** get the same basic vector.

**Problem:** The model cannot directly represent the different meanings of `bank`.

Examples of static embeddings include **Word2Vec** and **GloVe**.

### 2️⃣ Contextual Meaning

The representation of a word can change based on the **surrounding context**.

```text
"I deposited money in the bank."
                    ↓
              financial meaning


"The river bank is beautiful."
            ↓
        riverside meaning
```

So the model produces **different contextual representations** for `bank`.

### 🔑 Remember

```text
Static:
word → fixed vector

Contextual:
word + context → context-dependent representation
```

> **Static embeddings represent a word independently of context.**

> **Contextual representations capture what the word means in its specific context.**

---

## 9. Bias in Embeddings

**Embedding bias** occurs when the vectors learned by a model reflect **biases present in the training data**.

### 🧠 Example

Suppose training data contains many sentences associating:

```text
"doctor" → male
"nurse"  → female
```

The model may learn a relationship between these concepts in its embedding space.

```text
Doctor ───── Male
Nurse  ───── Female
```

This doesn't mean the model was explicitly told this rule. It can **learn the association from patterns in the data**.

### 🔄 Where Does Bias Come From?

```text
Training Data
     ↓
Existing human biases
     ↓
Model learns patterns
     ↓
Embeddings
     ↓
Potential biased associations
```

Bias can come from:

- Historical/social biases in data
    
- Imbalanced representation
    
- Stereotypes in text
    
- Biased labeling or datasets
    

### ⚠️ Important

Embeddings don't inherently "understand" that a relationship is **fair, unfair, true, or false**.

They learn statistical patterns from data.

### 🔑 Remember

> **Embedding bias = biases or stereotypes in the training data can become reflected in learned vector representations.**

> **Garbage/bias in the data can lead to biased representations and outputs.**

---

## 10. Keyword Search vs Embedding Search

The main difference is:

> **Keyword search looks for matching words. Embedding search looks for similar meaning.**

### 🔤 Keyword Search

Searches for **exact or closely matching words**.

```text
Query:
"How to fix database connection error?"

        ↓

Find documents containing:
"database"
"connection"
"error"
```

It may miss:

```text
"How do I resolve a PostgreSQL connectivity problem?"
```

because the exact words are different.

### 🧠 Embedding Search

Converts the query and documents into **vectors**, then finds vectors that are close in meaning.

```text
Query
   ↓
Embedding
   ↓
[0.21, 0.73, -0.12, ...]

Documents
   ↓
Embeddings
   ↓
Compare vectors
   ↓
Most semantically similar results
```

So:

```text
"database connection error"
              ≈
"PostgreSQL connectivity problem"
```

even though the exact words differ.

### ⚖️ Comparison

||Keyword Search|Embedding Search|
|---|---|---|
|Focus|Words|Meaning|
|Exact words important?|✅ Yes|❌ Not necessarily|
|Understands synonyms?|Limited|✅ Better|
|Uses vectors?|❌|✅|
|Good for|Exact terms, names, IDs|Semantic/conceptual search|

### 🔑 Remember

```text
Keyword Search
Query → Match Words → Results

Embedding Search
Query → Vector → Compare Meaning → Results
```

> **Keyword search asks: "Where are these words?"**

> **Embedding search asks: "Where is similar meaning?"**

---

## 11. Applications of Embeddings

Embeddings are useful because they convert complex information into **vectors**, allowing us to mathematically compare and organize it.

### 1️⃣ Recommendation Systems

Items with similar embeddings can be recommended to users.

```text
User likes → Movie A
               ↓
        Find similar vectors
               ↓
      Movie B, Movie C
```

Example: If you like a sci-fi movie, the system can find movies with **similar embeddings**.

---

### 2️⃣ Clustering

Similar data points can be grouped together based on their embeddings.

```text
Embeddings
    ↓
Similarity / Distance
    ↓
┌───────┐   ┌───────┐
│ Group │   │ Group │
│   A   │   │   B   │
└───────┘   └───────┘
```

Example:

```text
Technology articles → Cluster 1
Sports articles     → Cluster 2
Politics articles   → Cluster 3
```

---

### 3️⃣ RAG (Retrieval-Augmented Generation)

Embeddings help **find relevant information** from a knowledge base.

```text
User Query
    ↓
Query Embedding
    ↓
Vector Search
    ↓
Relevant Documents
    ↓
LLM
    ↓
Answer
```

Example:

> "What is our company's leave policy?"

The query embedding is compared with document embeddings to find the most relevant policy.

---

### 4️⃣ Multimodal Embeddings

Different types of data can be converted into vectors in a **shared or compatible embedding space**.

```text
Text ──────→ Embedding ──┐
                         │
Image ─────→ Embedding ──┼→ Compare / Search
                         │
Audio ─────→ Embedding ──┘
```

For example:

```text
"dog playing in a park" → Text Vector
        ↕
Image of a dog in a park → Image Vector
```

If the model is trained for aligned multimodal embeddings, these vectors can be compared because they represent related concepts in a compatible space.

### 🔑 Remember

> **Embeddings turn information into vectors that can be compared, grouped, retrieved, and matched.**

```text
Recommendation → Find similar items
Clustering     → Group similar items
RAG            → Find relevant information
Multimodal     → Connect different data types
```