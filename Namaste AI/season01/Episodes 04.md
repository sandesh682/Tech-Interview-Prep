
## 1. What is the "Secret Language" of LLMs?

LLMs don't understand text directly like humans do. They process **numbers**.

```text
Human Language
      ↓
   Tokenizer
      ↓
    Tokens
      ↓
 Token IDs
      ↓
Numbers / Vectors
      ↓
     LLM
```

For example:

```text
"I love AI"
     ↓
Tokens
     ↓
["I", " love", " AI"]
     ↓
Token IDs
     ↓
[40, 1842, 955]  ← illustrative
```

The LLM performs its calculations using these **numerical representations**, not directly on English words.

### 🔑 Remember

> **Humans communicate using language; LLMs process numerical representations of language.**

The "secret language" is therefore **not a separate language**. It is the numerical representation of tokens that the neural network works with.

---

## 2. What are Tokens?

A **token** is a small piece of text that an LLM processes.

A token can be:

- A complete word
    
- Part of a word
    
- Punctuation
    
- Sometimes spaces or special characters
    

### Example

```text
"ChatGPT is amazing!"

        ↓

["Chat", "GPT", " is", " amazing", "!"]
```

So, **1 token ≠ always 1 word**.

A long or uncommon word may be split into multiple tokens.

### 🔑 Remember

> **Tokens are the basic units of text that an LLM processes.**

```text
Text → Tokens → Token IDs → Numbers → LLM
```

---

## 3. What is a Tokenizer?

A **Tokenizer** converts human-readable text into **tokens and their corresponding Token IDs** that an LLM can process.

```text
Text
 ↓
Tokenizer
 ↓
Tokens
 ↓
Token IDs
 ↓
LLM
```

### Example

```text
"I love AI"

      ↓
   Tokenizer
      ↓
["I", " love", " AI"]
      ↓
[40, 1842, 955]  ← illustrative IDs
```

### What does the Tokenizer do?

1. **Splits text into tokens**
    
2. **Maps each token to a unique Token ID** using its vocabulary
    

```text
"I love AI"
    ↓
Tokenization
    ↓
["I", " love", " AI"]
    ↓
Token → Token ID
    ↓
[40, 1842, 955]
```

### 🔑 Remember

> **Tokenizer = Text → Tokens → Token IDs**

The **LLM then processes these numerical representations** to generate the next token.

---

## 4. What is Subword Tokenization?

**Subword tokenization** is a technique where words are split into **smaller meaningful pieces (subwords)** instead of treating every word as a single token.

### Example

```text
"unhappiness"

       ↓

["un", "happiness"]
```

Or:

```text
"playing"

   ↓

["play", "ing"]
```

The exact split depends on the tokenizer and its vocabulary.

### 🤔 Why use Subword Tokenization?

It solves a major problem with whole-word tokenization:

> **There are too many possible words to store as individual tokens.**

With subwords:

- Common words → can remain as a single token
    
- Uncommon/new words → can be split into smaller pieces
    
- Vocabulary size stays manageable
    
- The model can handle words it hasn't seen exactly before
    

### Example

Suppose the tokenizer knows:

```text
play
playing
ed
ing
```

If it encounters:

```text
"playfulness"
```

It may break it into pieces such as:

```text
play + ful + ness
```

instead of needing `"playfulness"` as a separate vocabulary entry.

### 🔑 Remember

> **Subword Tokenization = Breaking words into smaller pieces so the tokenizer can efficiently represent a much larger variety of words.**

```text
Word
 ↓
Subwords
 ↓
Token IDs
 ↓
LLM
```

---

## 5. What is BPE?

**BPE = Byte Pair Encoding**

BPE is a **subword tokenization algorithm** that builds a vocabulary by repeatedly merging the **most frequent pair of characters/subwords**.

### Simple Example

Suppose the training data contains:

```text
low
lower
lowest
```

Initially:

```text
l o w e r
```

If `l + o` frequently appears, BPE can merge them:

```text
lo w e r
```

Then frequently occurring pairs can be merged further:

```text
low er
```

Eventually, common patterns become tokens in the vocabulary.

### 🔑 Idea

> **BPE starts with small units and repeatedly merges frequently occurring pairs to create larger subword tokens.**

---

## Other Tokenization Methods

|Method|Basic Idea|
|---|---|
|**BPE**|Repeatedly merges the most frequent pair of tokens.|
|**WordPiece**|Similar to BPE, but chooses merges based on a likelihood-based objective. Used by models such as BERT.|
|**Unigram**|Starts with a large vocabulary and removes tokens that contribute least to the model's likelihood.|
|**SentencePiece**|A tokenization framework that can implement algorithms such as **BPE and Unigram** and can work directly on raw text without requiring whitespace-based word splitting.|

### 🧠 Remember

```text
Subword Tokenization
        ↓
 ┌──────┼────────┐
 ↓      ↓        ↓
 BPE  WordPiece  Unigram
```

> **BPE is an algorithm for creating subword tokens. SentencePiece is primarily a tokenization framework that can use algorithms such as BPE or Unigram.**

---

## 6. English vs Other Languages: Tokenization

LLMs don't tokenize every language equally efficiently.

### 🇬🇧 English

English generally has **relatively efficient tokenization** because many common English words and word pieces occur frequently in training data.

```text
"playing football"

        ↓

["playing", " football"]
```

Common words may often be represented using fewer tokens.

---

### 🌍 Other Languages

Languages such as **Hindi, Marathi, Japanese, Chinese, etc.** can sometimes require **more tokens to represent the same amount of text**, depending on the tokenizer and model.

For example:

```text
English:
"I am learning AI"

        ↓

Fewer tokens


Hindi:
"मैं AI सीख रहा हूँ"

        ↓

Potentially more tokens
```

The exact number depends on the **model's tokenizer and vocabulary**.

### 🤔 Why does this happen?

Tokenizers learn their vocabulary from training data.

If a language has **less representation in the tokenizer's training data**, its words may be split into smaller pieces.

```text
Common pattern
     ↓
Single / larger token

Less common pattern
     ↓
Multiple smaller tokens
```

### 💰 Why does tokenization matter?

More tokens mean:

- More computation
    
- More context-window usage
    
- Potentially higher API cost when pricing is token-based
    
- Less text can fit into a fixed context window
    

### 🔑 Remember

> **The same sentence can use different numbers of tokens depending on the language and tokenizer.**

```text
Same Meaning
     ↓
Different Language
     ↓
Different Tokenization
     ↓
Different Number of Tokens
```

---

## 7. Emojis, Special Characters & Whitespace Tokenization

A tokenizer doesn't only tokenize **words**. It also handles **punctuation, emojis, spaces, and special characters**.

### 😊 Emojis

An emoji can be represented by **one or multiple tokens**, depending on the tokenizer.

```text
"Hello 😊"

      ↓

["Hello", " 😊"]
```

Some complex emojis may require multiple tokens.

---

### 🔣 Special Characters

Characters such as:

```text
@  #  $  %  &  +  =  {  }  <  >
```

can also become tokens or parts of tokens.

Example:

```text
"hello@world.com"

       ↓

["hello", "@", "world", ".", "com"]
```

The exact tokenization depends on the tokenizer.

---

### ␠ Whitespace

Whitespace can also be part of a token.

For example, some tokenizers may distinguish:

```text
"Hello"
" Hello"
```

because the **leading space** can be encoded as part of the token.

This allows the tokenizer to represent common word patterns efficiently.

### 🔑 Remember

> **Tokens are not necessarily words.**

They can represent:

```text
Words
Subwords
Punctuation
Emojis
Special characters
Whitespace
```

The exact tokenization depends on the **tokenizer and its vocabulary**.

---

## 8. What are Special Tokens?

**Special tokens** are predefined tokens used by a tokenizer/model to represent **specific control or structural information**, rather than normal text.

### Examples

|Special Token|Purpose|
|---|---|
|`<BOS>`|**Beginning of Sequence** — marks the start of text|
|`<EOS>`|**End of Sequence** — marks the end of text|
|`<PAD>`|**Padding** — makes sequences the same length|
|`<UNK>`|**Unknown** — represents an unsupported/unknown token|
|`<SEP>`|**Separator** — separates different parts of input|

> **Note:** The actual names and availability of special tokens depend on the model/tokenizer.

### Example

```text
<BOS> I love AI <EOS>
  ↑              ↑
Start           End
```

Special tokens can also be used for **chat structure**, such as separating system instructions, user messages, and assistant responses.

### 🔑 Remember

> **Normal tokens → represent text**  
> **Special tokens → provide instructions/structure to the model**

```text
Text + Special Tokens
        ↓
     Tokenizer
        ↓
     Token IDs
        ↓
       LLM
```

---

## 9. What is the Context Window?

The **context window** is the maximum number of **tokens an LLM can process for a particular response**.

It is **not limited to one message**. It can include:

```text
System Instructions
       +
Conversation History
       +
Current Message
       +
Files / Tool Results
       ↓
   Context Window
       ↓
    LLM Response
```

### Example

If the context window is **100,000 tokens**:

```text
Message 1 → 2,000 tokens
Message 2 → 3,000 tokens
Message 3 → 5,000 tokens
        ...
        ↓
Total context must fit within
100,000 tokens
```

### 🧠 Simple Analogy

> **Context Window = LLM's working desk.**

The model can work with information currently **on the desk**, but it doesn't mean that information becomes permanent memory.

### 🔑 Remember

> **Context Window = Maximum tokens the model can consider in a single context/response.**

**One message ≠ one context window.**  
Multiple messages can together form the context.

---

### 📦 Context Window = Input + Output

The context window is **not only for input tokens**. The model also needs capacity for the **generated output**.

```text
Context Window
┌───────────────────────────────┐
│ Input Tokens                  │
│                               │
│ • Conversation history        │
│ • Current prompt              │
│ • File / relevant file data   │
│ • Tool results                │
│                               │
├───────────────────────────────┤
│ Output Tokens                 │
│                               │
│ • AI's generated response     │
└───────────────────────────────┘
```

### Example

Suppose a model supports **10,000 tokens**:

```text
Input Context  → 8,000 tokens
Output         → up to 2,000 tokens
────────────────────────────
Total          → 10,000 tokens
```

The exact input/output limits depend on the model, and some systems impose a separate maximum output limit.

### 📄 What About Files?

Suppose your code file contributes **1,000 tokens**.

When you ask another question about that file, relevant file content may again be included in the model's context:

```text
Previous Conversation
        +
Relevant File Content
        +
New Question
        ↓
    Input Tokens
        ↓
       LLM
        ↓
Generated Answer
        ↓
    Output Tokens
```

So reading a file once does **not mean the LLM permanently stores it internally**.

### 🔑 Remember

> **Context Window = Input Context + Generated Output**

And:

> **Input isn't just your latest message — it can include conversation history, relevant file content, instructions and tool results.**