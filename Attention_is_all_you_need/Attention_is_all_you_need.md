# Paper Notes: "Attention Is All You Need"

## Introduction

The paper "Attention Is All You Need" by Vaswani et al., published in 2017, introduces a revolutionary neural network architecture known as the Transformer. This architecture is uniquely based on self-attention mechanisms, eliminating the need for recurrent neural networks (RNNs) and convolutions entirely.

## Key Contributions

### Transformer Architecture
- The Transformer model consists of an encoder and a decoder, both of which rely solely on self-attention mechanisms to process input sequences. This architecture is simpler and more parallelizable than traditional sequence transduction models based on RNNs or convolutions.

### Self-Attention Mechanism
- Self-attention, also known as intra-attention, allows the model to relate different positions of a single sequence to compute a meaningful representation of the sequence. This is achieved without the sequential dependencies inherent in RNNs, enabling parallel processing and significant speed improvements.

## Attention Mechanism

### Basic Attention Function
- The attention function takes in three types of vectors: **query** ($$q$$), **key** ($$k$$), and **value** ($$v$$). The output is a weighted sum of the values, where the weights are computed based on the similarity between the query and the keys.
  $$
  \text{Attention}(Q, K, V) = \text{softmax} \left( \frac{QK^T}{\sqrt{d_k}} \right) V
  $$
  Here, $$Q$$, $$K$$, and $$V$$ are matrices packed with query, key, and value vectors, respectively. The scaling factor $$\frac{1}{\sqrt{d_k}}$$ normalizes the dot products to prevent large values.

### Scaled Dot-Product Attention
- This is the specific attention mechanism used in the Transformer. It is faster and more space-efficient compared to additive attention, which uses a feed-forward network with a single hidden layer.

### Multi-Head Attention
- To allow the model to jointly attend to information from different representation subspaces at different positions, the Transformer uses multi-head attention. This involves computing multiple attention scores (typically 8 heads) and then concatenating and linearly projecting the results back to the original dimension.
  - Each head computes attention scores independently, allowing the model to capture different aspects of the input sequence.

## Applications of Attention in the Transformer

### Encoder-Decoder Attention
- In the decoder, the queries come from the previous decoder layer, while the keys and values come from the output of the encoder. This allows every position in the decoder to attend over all positions in the input sequence.

### Self-Attention in Encoder and Decoder
- Both the encoder and decoder use self-attention layers to process their input sequences. In self-attention, the keys, values, and queries are all derived from the same input sequence.

## Visualization of Transformer Architecture

Here is a representation of the Transformer architecture:

![](transformer.png "Transformer")