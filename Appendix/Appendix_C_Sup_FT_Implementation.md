# C SUP-FT IMPLEMENTATION DETAILS



## Model Architecture

Sup-FT employs two independent XLM-RoBERTa-base encoders (125M parameters each) to process (i) paragraph text and (ii) LLM-generated technique-focused explanations. The two streams are fused via bidirectional cross-attention and a feature-fusion MLP before the final 23-label classification head.

## Cross-Attention

We use bidirectional multi-head attention with dmodel = 768 and h = 8 heads. Let H ∈ R^(B×L×768) denote encoder hidden states. Text-to-explanation attention is:

Attn_T→E(Q = H_text, K = H_expl, V = H_expl),

and explanation-to-text attention is:

Attn_E→T(Q = H_expl, K = H_text, V = H_text).

## Feature Fusion

We concatenate four [CLS] embeddings h_text; h_expl; h_T→E^[CLS]; h_E→T^[CLS] and pass them through a two-layer MLP with ReLU activations. Dropout rates are 0.2 (first layer) and 0.1 (second layer). The final classifier is a linear projection W_c ∈ R^(23×768).

## Training Configuration

We use AdamW (β1 = 0.9, β2 = 0.999, weight decay 10^-3) with learning rate 1 × 10^-5, 1000-step linear warmup, and linear decay. Physical batch size is 8 with 4-step gradient accumulation (effective batch size 32). We apply gradient clipping (0.5) and enable gradient checkpointing.

## Loss and Class Weights

We optimize weighted binary cross-entropy. Technique-specific weights are computed as:

w_t = min(3 · n_t_neg / n_t_pos, 30),

where n_t_pos and n_t_neg are positive/negative counts for technique t.

## Sequence Lengths and Early Stopping

Maximum sequence length is 256 tokens for text and 128 tokens for explanations. We train up to 10 epochs with early stopping on validation Micro F1 (patience 3). Experiments run on NVIDIA A40 GPUs (48GB).
