https://arxiv.org/pdf/2307.13269.pdf

我们可以先获得若干 LoRA，$w_1=A_1B_1,\dots w_n= A_nB_n$，然后使用 adapt-compose 方法将它们合并起来。

compose 即计算 $(\sum_{i=1}^n c_iA_i)(\sum_{i=1}^n c_iB_i)$ 并和 LLM 合并

adapt 是训练 $c_1,\dots c_n$ 的过程，这里使用了一个 gradient-free method 叫作 CMA-ES

注意一下这个 pipeline：首先我们从 intended task 中进行一些 sample（5 个），然后从已经有的大量 LoRA 中随机挑选几个出来，然后进行上述训练，完成训练并与 backbone model 合并之后得到静态的模型，再拿去 inference。

文中写了三个 limitation/future works

1.系数的训练方式
2.LoRA Hub 只能用于 Decoder-only model
3.LoRA 模块是随机选出来的，而且是在见到 task 之前确定好的。