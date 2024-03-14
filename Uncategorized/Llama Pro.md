https://arxiv.org/pdf/2401.02415.pdf

我们知道大模型中都有若干 Multihead self attention(mhsa) 模块的堆叠。本文作者在预训练好的 LLaMA 的 mhsa 块后面添加了一些 mhsa 块来进行模型能力增强，后增加的 Module 可以由下图右侧表示：

![image](https://img2024.cnblogs.com/blog/1797571/202403/1797571-20240314094821037-174847917.png)

在 fine tuning 过程中，我们冻结 LLaMA Block 并训练这些 identity copy，这次训练的开始阶段输出和不添加 identity copy 是一样的，数据只会通过 residual 传播，因为 mhsa 里面有 zero-linear。

冻结 LLaMA 的原始参数相当于保护了 LLM 的语言建模能力，而下游任务的信息量在语言建模能力的基础上并不需要很多神经元就可以执行。