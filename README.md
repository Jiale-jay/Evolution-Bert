# Evolution-Bert
进化 Bert

进化 Bert
Bert是谷歌2018年发布的语言模型，它证明了一个非常深的模型可以显著提高NLP任务的准确率，而且模型可以通过无需标记的文本数据训练得到，它大幅度提升了各项NLP任务的线上结果。BERT是构建于Transformer之上的预训练语言模型，它的特点之一就是所有层都联合上下文语境进行预训练。

Bert之前在NLP领域一直属于霸主级别的地位，原因是它又深效果又好，新晋的NLP算法都很难与基于Bert调参的模型抗衡，所以开源社区愈发倾向于使用基于Bert迁移学习的模型。

https://github.com/google-research/bert

任务2
由于Bert拥有对中文进行支持的预训练模型，在这一阶段要求使用Bert提供的预训练模型，构建中日和英日的翻译器，观察模型的性能表现，从Bert的实现原理猜测为什么不同语言会出现性能差异？

中文和东亚文字在NLP当中的特殊性
Whole Word Masking (wwm)，暂翻译为全词Mask或整词Mask，是谷歌在2019年5月31日发布的一项BERT的升级版本，主要更改了原预训练阶段的训练样本生成策略。 简单来说，原有基于WordPiece的分词方式会把一个完整的词切分成若干个子词，在生成训练样本时，这些被分开的子词会随机被mask。 在全词Mask中，如果一个完整的词的部分WordPiece子词被mask，则同属该词的其他部分也会被mask，即全词Mask。

同理，由于谷歌官方发布的BERT-base, Chinese中，中文是以字为粒度进行切分，没有考虑到传统NLP中的中文分词（CWS）。 这也是导致使用传统的Transformer模型处理中文时效果稍差的一个原因。中文分词是一个需要大量数据积淀的工作。目前包括腾讯AI实验室、百度AI实验室以及各所高校都发布了自己的词向量/分词模型。

哈工大讯飞联合实验室发布的Pre-Training with Whole Word Masking for Chinese BERT（中文BERT-wwm系列模型）针对中文语料进行了特别优化的训练，它的规模之大以至于用单张V100大约需要花费10万小时。

词粒度的差异使得我们在任务2中两种语言的成效有所区别，因此，我们有必要尝试在这种模型下的性能。

任务3
使用CBERT-wwm对cmrc2018篇章片段抽取型阅读理解数据进行训练，评价流程请参考：

https://worksheets.codalab.org/worksheets/0x96f61ee5e9914aee8b54bd11e66ec647/

数据集：

https://worksheets.codalab.org/worksheets/0x92a80d2fab4b4f79a2b4064f7ddca9ce

任务4
AI的兴起带来的不仅是科技界的颠覆，同时也会影响人文社科的方方面面。民众对AI的看法也在AI兴潮中随着时间推移有所改变。从不信任，到拥护，到思考伦理问题……

Public Perception of Artificial Intelligence是微软研究院发布的数据集，其作用是对30年来NYT杂志对AI观点的情绪的总结。

Analyses of text corpora over time can reveal trends in beliefs, interest, and sentiment about a topic. We focus on views expressed about artificial intelligence (AI) in the New York Times over a 30-year period. General interest, awareness, and discussion about AI has waxed and waned since the field was founded in 1956. We present a set of measures that captures levels of engagement, measures of pessimism and optimism, the prevalence of specific hopes and concerns, and topics that are linked to discussions about AI over decades. We find that discussion of AI has increased sharply since 2009, and that these discussions have been consistently more optimistic than pessimistic. However, when we examine specific concerns, we find that worries of loss of control of AI, ethical concerns for AI, and the negative impact of AI on work have grown in recent years. We also find that hopes for AI in healthcare and education have increased over time. This is joint work with E. Fast and E. Horvitz published at AAAI 2017.

尝试用你迄今为止学过的算法训练一个分类器，对robot-ai-all-public.csv中的文段所隐含的积极/消极态度进行分类，并且获取一个成绩最好的模型。
