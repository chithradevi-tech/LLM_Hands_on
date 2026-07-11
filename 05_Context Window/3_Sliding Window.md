# Sliding Window

## What is Sliding Window?

**Sliding Window** is a technique used to **process long text that exceeds the model's context length** by moving a fixed-size window over the text, one section at a time.

Instead of processing the entire document at once, the model processes **small overlapping chunks**.

---

## Simple Definition

> **Sliding Window processes long text by reading it in overlapping chunks instead of all at once.**

---

# Why Do We Need Sliding Window?

Suppose an LLM has:

```text
Context Length = 8,000 tokens
```

But your document contains:

```text
20,000 tokens
```

The model cannot process all 20,000 tokens together.

So we split the document into smaller windows.

---

# How Sliding Window Works

Suppose we choose:

* Window Size = **4,000 tokens**
* Overlap = **500 tokens**

Document:

```text
1 ─────────────────────────────── 20,000
```

### Window 1

```text
1 -------------------- 4000
```

### Window 2

```text
3501 -------------------- 7500
```

Notice that **500 tokens overlap** with the previous window.

### Window 3

```text
7001 -------------------- 11000
```

This process continues until the entire document is covered.

---

# Visual Diagram

```text
Document

|------------------------------------------------------------|

Window 1
|==============|

        Window 2
        |==============|

                Window 3
                |==============|

                        Window 4
                        |==============|
```

The overlapping area ensures that important context isn't lost.

---

# Why Use Overlap?

Suppose a sentence is split between two chunks.

Without overlap:

```text
Chunk 1:
The customer submitted the

Chunk 2:
application yesterday.
```

The model loses the complete sentence.

With overlap:

```text
Chunk 1:
The customer submitted the application

Chunk 2:
submitted the application yesterday.
```

Now both chunks contain enough context.

---

# Example

Document:

```text
Page 1
Page 2
Page 3
Page 4
Page 5
```

Window size:

```text
2 pages
```

Overlap:

```text
1 page
```

Processing:

```text
Window 1:
Page1 Page2

Window 2:
Page2 Page3

Window 3:
Page3 Page4

Window 4:
Page4 Page5
```

---

# Applications

Sliding Window is commonly used in:

* ✅ RAG (Retrieval-Augmented Generation)
* ✅ Long document summarization
* ✅ PDF processing
* ✅ Legal document analysis
* ✅ Medical reports
* ✅ Large codebase analysis

---

# Advantages

* ✅ Handles documents larger than the context window.
* ✅ Preserves context using overlap.
* ✅ Reduces information loss.
* ✅ Improves retrieval quality in RAG.

---

# Disadvantages

* ❌ Some text is processed multiple times because of overlap.
* ❌ More computation and memory usage.
* ❌ Choosing the right window size and overlap is important.

---

# Sliding Window vs Fixed Chunking

| Fixed Chunking                       | Sliding Window                    |
| ------------------------------------ | --------------------------------- |
| Splits into separate chunks          | Splits into overlapping chunks    |
| May lose context at chunk boundaries | Preserves context with overlap    |
| Simpler                              | Better for long documents and RAG |

---

> **Sliding Window is a technique for processing documents that are larger than an LLM's context length. The document is divided into overlapping chunks, and each chunk is processed separately. The overlap preserves context between chunks, making it especially useful for RAG, document summarization, and long-text processing.**

---

# Easy Memory Trick

Imagine reading a long book with a small bookmark.

* 📖 You read **3 pages** at a time.
* Before moving forward, you **re-read the last page**.

Example:

```text
Pages:
1 2 3

Move

3 4 5

Move

5 6 7
```

The repeated page helps you remember the story.

That's exactly how a **Sliding Window** works.

---

> **Sliding Window processes long text in overlapping chunks, allowing LLMs to handle documents that exceed their context length while preserving context between chunks.**
