- NLP（Natural Langugae Processing）：自然语言处理
- SOTA（State-of-the-Art）：特定领域技术先进、表现最好、性能最优的产品、模型、技术方案等
- 神经网络：
  - CNN：卷积神经网络（处理图像）
  - RNN（Recurrent Neural Network）：循环神经网络（处理序列）
    - 隐状态
- BLEU(Bilingual Evaluation Understudy（双语评估替补）：让机器生成的文本（候选文本）与一个或多个参考答案（人工参考译文）进行 n-gram 重叠度的比较，重叠越多，得分越高。
- **Seq2Seq（sequence transduction models）**：序列转换模型
	- encoder编码器：读入句子，输出一个上下文感知的表征向量（Context Vectors），提取语义信息、建模序列内部依赖关系
	- decoder解码器：读入已生成的部分输出（如已翻译的句子），输出下一个 token 的概率分布，自回归地预测序列中的下一个词或token「这是目前 Transformer Decoder 的核心工作模式（生成完第一个，再拿第一个当已知条件去猜第二个，如此循环）」
   -  以往的Seq2Seq的是通过RNN来实现的，但存在几个根本性的挑战:
      1. 长距离依赖：RNN通过隐状态传递信息，但随着序列长度增加，早期信息会逐渐衰减
      2. 固定长度瓶颈：固定上下文向量需要承载所有源序列的信息，Cho等人(2014)的实验表明，随着句子长度增加，翻译质量显著下降。
      3. 顺序计算限制：RNN必须按时间步顺序计算，无法并行化，训练效率低下
- **注意力机制：**
  - 2015年，Bahdanau等人在论文”Neural Machine Translation by Jointly Learning to Align and Translate”中首次提出了注意力机制，用于解决机器翻译中的固定长度瓶颈问题。
	- 核心思想：在生成每个目标词时，不再使用固定的上下文向量，而是动态地”关注”源序列的不同部分。
