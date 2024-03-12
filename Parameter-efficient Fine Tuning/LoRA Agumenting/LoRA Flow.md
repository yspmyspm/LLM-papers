迭代了一下上面 LoRAHub 的实现方式，考虑每个 layer（就是 attention block+FFN）的 input $x_t$，将它另外通过一个 fusion gate，得到 LoRA 的组合系数。同时 LoRA Hub 将 AB 视为不同的 Subpart，这里是直接将 LoRA 的 output 使用系数组合起来

假设有 $k$ 个 LoRA 待组合，输入向量 $x_t$ 是 $d\times 1$ 的，那么 fusion gate 的输出就是 $softmax(W_tx_t) + b_t$，其中 $b_t$ 是 $k\times 1$ 的向量，而 $W_t$ 是 $k\times d$ 的向量。