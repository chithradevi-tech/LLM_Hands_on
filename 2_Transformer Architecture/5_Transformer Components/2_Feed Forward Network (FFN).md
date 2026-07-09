Feed Forward Network (FFN) is a core component of every Transformer layer.

It comes after the Attention mechanism and helps the model learn deeper patterns and transformations from the attention output.

### What is FFN?

FFN is a small neural network applied independently to each token.

Attention finds which words are important; FFN learns what to do with that information.

### Simple Definition

FFN transforms the attention output into a richer representation using neural network layers.

### Where does FFN appear in a Transformer?

### How FFN Works

### Step 1: Input from Attention

Suppose attention produces a vector for a token.

### Step 2: First Linear Layer

The vector is expanded to a larger dimension.

Example:

### Step 3: Activation Function

A non-linear function such as ReLU or GELU is applied.

### Step 4: Second Linear Layer

The vector is projected back to the original size.

### FFN Formula

Where W1 and W2 are trainable weight matrices.

### Visual Flow

### Why is FFN Needed?

| Attention                         | FFN                         |
| --------------------------------- | --------------------------- |
| Finds relationships between words | Learns complex patterns     |
| Decides what is important         | Decides how to represent it |
| Focuses on context                | Improves feature learning   |

### Example

Sentence:

"The cat sat on the mat."

Attention may learn that "cat" is related to "sat".

FFN then transforms that information into a richer representation that helps the model understand grammar and meaning better.

### Advantages of FFN

* ✅ Adds non-linearity.

* ✅ Learns complex features.

* ✅ Improves model capacity.

* ✅ Applied to every token independently.

* ✅ Essential for high-quality language understanding.

### Interview Answer (30 Seconds)

Answer

Feed Forward Network (FFN) is a neural network layer used after the attention mechanism in a Transformer. It consists of two linear layers with a non-linear activation such as ReLU or GELU in between. The FFN transforms the attention output into a richer representation, helping the model learn complex patterns and improve language understanding.

### Easy Memory Trick

Think of a classroom:

* Attention = Students decide which information is important.

* FFN = Each student processes and understands that information deeply.


FFN takes the output of attention and uses a small neural network to learn richer, more meaningful representations for each token.
