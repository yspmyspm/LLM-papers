
<details>
<summary>survey</summary>

https://arxiv.org/pdf/2308.10792.pdf

在大规模自回归预训练之后 LLM 拥有了语言建模的能力，也就是说了上句能跟上下句。但是如果让 LLM 回答一些问题，或者实现 Chat 的功能，却还不太现实。所以我们通过 instruction tuning 来实现这个功能。

![image](https://img2024.cnblogs.com/blog/1797571/202403/1797571-20240310103421463-606640774.png)

综述本身就是对着这张图介绍的。

对于 dataset construction 有 [人手写](https://instructions.apps.allenai.org/) 和 LLM 生成两种方法。这些 dataset 的相当于是解决上百个 NLP task 的 instruction，同时必然存在 cross-lingual 的内容。每个 dataset 都遵循某种格式，比如 `(input,output)` 或者`(input,answer choice,target)`

<details>
<summary>为了做 data agumentation，人们也确实是绞尽脑汁</summary>

3.7 Evol-Instruct Evol-Instruct（Xu等人，2023a）是一个英语指令数据集，包含一个由52K条指令组成的训练集和一个由218条指令组成的评估集。作者提示ChatGPT（OpenAI，2022）使用深入和扩展的演变策略来重写指令。深入演变策略包括五种操作，例如添加约束、增加推理步骤、复杂化输入等。扩展演变策略将简单指令升级为更复杂的指令，或者直接生成新的指令以增加多样性。

作者首先使用52K（指令，响应）对作为初始集。然后他们随机采样一个演变策略，并要求ChatGPT根据选择的演变策略重写初始指令。作者利用ChatGPT和规则过滤掉没有演变的指令对，并用新生成的演变指令对更新数据集。在重复上述过程4次后，作者收集了250K指令对。除了训练集之外，作者还从真实场景（例如开源项目、平台和论坛）收集了218条人类生成的指令，称为Evol-Instruct测试集。
</details>

更前沿的方法是使用 ChatGPT 扮演不同的角色生成数据。


</details>


https://github.com/SinclairCoder/Instruction-Tuning-Papers 这个 repository 收录了大量 instruction tuning 的论文。
