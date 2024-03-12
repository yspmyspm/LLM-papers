Motivation: 对于那些已经在训练集中已经出现过的工具，LLM 的使用正确率只有 30%~60%，远远低于预期。

做法：Simulated trial and error，也就是在让 LLM 去积极地想象一些使用场景，形成一些使用工具的经验。通过 long-term 和 short-term memory 分别进行 广度 和 深度的探索

具体做法两张图比较好的描绘了这个方法。

![image](https://img2024.cnblogs.com/blog/1797571/202403/1797571-20240311211901796-1587754088.png)

这张图在工程层面上具体描述了这个做法的落地细节，感觉有了 idea 直接嗯编就没啥问题。

![image](https://img2024.cnblogs.com/blog/1797571/202403/1797571-20240311211844781-923051674.png)