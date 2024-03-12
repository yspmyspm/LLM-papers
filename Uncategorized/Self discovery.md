https://arxiv.org/pdf/2402.03620.pdf

这篇工作注意到了之前的 CoT 或者 step-back prompting 都在不同方面取得了成功，同时又认为这些 prompting 手段本质上是一个任务解决的原子操作。如果把一个任务解决看作一个分子，那么这个分子的组成可能需要不同的原子。我们并不人为规定 NLP tasks 的解决框架，而是给 LLM 一些 prompt。

<details>
<summary>这是所有可能得 prompt 列表，可以发现它们来自另一篇论文</summary>

![image](https://img2024.cnblogs.com/blog/1797571/202403/1797571-20240312163537953-1371806849.png)

</details>

沿着这个思路，研究人员设计了三个模块：

- Select

对于一个 task ，我们通过一个外挂 pre-trained module 来进行 prompt 筛选，选出与 task 相关的若干 prompt。

- Adapt

对于选出的 high-level prompts，我们使用大模型 依照任务具体情况 将它改写为可以提示模型思考的提问方式，这个部分也可以理解为搭建了一个任务的实现框架，比如什么时候问什么。

- Implement

通过填充任务解决框架，实现任务的解决。
