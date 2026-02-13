---
title: "FSRS算法学习摘录"
date: 2026-02-12
tags: [research]
---







本节摘选自[FSRS 是全世界最精确的间隔重复算法之一（最新基准测试更新）](https://zhuanlan.zhihu.com/p/692314506)

英文原文链接：[FSRS is one of the most accurate spaced repetition algorithms in the world (updated benchmark) : r/Anki](https://www.reddit.com/r/Anki/comments/1c29775/fsrs_is_one_of_the_most_accurate_spaced/?rdt=38151)

首先，任何「诚实」的间隔重复算法都必须能够预测在特定时间点**回忆**一张卡片的**概率**，这取决于卡片的复习历史。在下文中，我会用 **R** 来指代这个概率。

如果一个「不诚实」的算法不计算概率，只输出一个时间间隔，我们仍然可以在某些假设下将这个间隔转换为概率。虽然不是最理想，但总好过没有，因为这至少允许我们进行某种比较。这就是我们对 SM-2 算法所做的，它是基准测试中唯一的「不诚实」算法。我们决定不加入 [Memrise](https://memrise.zendesk.com/hc/en-us/articles/360015889057-How-does-the-spaced-repetition-system-work)，因为我们不确定所需的假设是否适用于将其间隔转换为概率。不过，即使加入了，它的表现也不会太好，它的灵活性极差，几乎不配被称为算法。

简言之，**诚实算法是基于概率来调整卡片的排程的，而非仅仅输出一个时间间隔**



本节选自[Paradoxes of Spaced Repetition Algorithms](https://l-m-sherlock.notion.site/Paradoxes-of-Spaced-Repetition-Algorithms-132c250163a18073a5d6eecdb2371ee5)

（我对本节非常认可）

# Paradoxes of Spaced Repetition Algorithms

The learner desires less repetition and more memorization. However, the algorithm requires more repetition to adapt to the learner.

The learner wants their true retention to accurately match their desired retention. However, the algorithm requires data from a diverse range of retention levels to improve sampling efficiency and avoid regression.

The learner may choose their rating based on the interval length. For instance, if they find a review easy but see that the "easy" interval is too long, they might select "good" instead. They may only choose "easy" for very simple cards. This behavior leads to higher retention on those cards, causing the algorithm to adjust and lengthen intervals. It creates a vicious cycle.

牛翻：

学习者希望减少重复、增加记忆。然而，算法需要通过更多重复来适应学习者的节奏。
学习者期望实际记忆留存率能精准匹配其预期目标。但算法需要收集不同留存水平的数据，以提升抽样效率并避免模型退化。
学习者可能根据复习间隔时长选择评分。例如，当感觉某次复习很简单，但发现"简单"选项对应的间隔过长时，他们可能会转而选择"良好"。或许只有面对极其简单的卡片时，他们才会选择"简单"。这种行为会导致这些卡片的留存率升高，进而促使算法调整并延长间隔，形成恶性循环。