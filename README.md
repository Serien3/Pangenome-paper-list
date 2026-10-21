## Preface

本仓库记录关于 Pangenome 的文章。看过的文章会至少用一句话概括内容，有些还会有 notes 。只有标题的就是还没看过的，只是先存档到这里。

### 🔥 Updates

- 2026-10 接下来主要关注泛基因组构建,以及泛基因组数据结构的相关工作

## Directory

⭐ 表示文章较多；🔥表示当前主要关注并更新

- ⭐🔥[Pangenome construction](#pangenome-construction)
- [Annotating pangenomes](#annotating-pangenomes)
- [Pangenome data structures](#pangenome-data-structures)
- [Sequence-to-graph mapping algorithms](#sequence-to-graph-mapping-algorithms)
  - [特异性/选择性计算思路](#特异性选择性计算思路)
- [Structural Variant callers](#structural-variant-callers)
- [Structural Variant genotypers](#structural-variant-genotypers)


# Pangenome

## Pangenome construction

1. [Genome Biology]**The design and construction of reference pangenome graphs with minigraph**[[paper]](https://doi.org/10.1186/s13059-020-02168-z) [[Github]](https://github.com/lh3/minigraph) [[reading-note]](paper-list/The%20design%20and%20construction%20of%20reference%20pangenome%20graphs%20with%20minigraph%20%5BR642E5L5%5D/reading-note.md)  minigraph 用 minimizer 种子 + 两级 chaining（段内线性链 DP 配 100kb 大 gap 罚分和 RMQ 混合加速，链间靠"最短 16 条游走中长度最接近查询间距"消歧选路）做无碱基比对的序列到图定位，再对链上锚点空隙打分（η·max gap）用 Ruzzo-Tompa 提候选分歧区、局部 pairwise 比对验证 ≥100bp INDEL 或 <80% 一致性后增广，从而在不用未实现的碱基级环图比对的前提下增量构造全基因组参考图。

2. [Nature Biotechnology]**Pangenome graph construction from genome alignments with Minigraph-Cactus**[[paper]](https://doi.org/10.1038/s41587-023-01793-w) [[Github]](https://github.com/ComparativeGenomicsToolkit/cactus) [[reading-note]](paper-list/Pangenome%20graph%20construction%20from%20genome%20alignments%20with%20Minigraph-Cactus%20%5B4P7UZ75D%5D/reading-note.md)  Minigraph-Cactus 先用 minigraph 构造 SV 骨架并将全部组装重新映射到同一张图，过滤可疑映射后按参考染色体拆分，再由 Cactus 合并匹配锚点、用 abPOA 细化锚点间序列并协调重排断点，通过 hal2vg 保留单倍型路径并补齐 SNP 和小 indel；最后裁剪长未对齐区段、按需过滤低频节点和建立索引，使 90 条人类单倍型的碱基级泛基因组可接入 Giraffe、DeepVariant 和 PanGenie，但仍依赖参考骨架且不涵盖跨染色体事件。

## Annotating pangenomes

## Pangenome data structures

1. [bioRxiv]**Billi: Accurate and Scalable Bubble Detection in Pangenome Graphs**[[paper]](https://www.biorxiv.org/content/10.1101/2025.11.21.689636v2) [[Github]](https://github.com/at-cg/billi) [[reading-note]](paper-list/Billi%20%5BLGBKWWZ6%5D/reading-note.md)  Billi 将允许环的变异区域分为双入口穿行的 panbubble 与单入口反向返回的 hairpin，通过限制 panbubble 内部的 hairpin 入口保证严格嵌套；把双向图转成辅助无向图，利用桥、环等价类和 DFS 祖先关系筛选候选，再回到双色边图验证方向可达性与最小性，给出精确枚举算法及只检查首个合适后继的可扩展启发式，在保留倒位及其内部小变异层级的同时扩展到 HPRC 大图，但启发式的完整性仅有已完成精确对照的测试支持。

## Sequence-to-graph mapping algorithms

### 特异性/选择性计算思路

1. [bioRxiv]**DCSMAP: A Hybrid Linear-Pangenome Framework for Accurate and Efficient Read Alignment**[[paper]](https://doi.org/10.64898/2026.10.18.759502) [[Github]](https://github.com/BGIResearch/dcsmap) [[reading-note]](paper-list/DCSMAP%20-%20A%20Hybrid%20Linear-Pangenome%20Framework%20for%20Accurate%20and%20Efficient%20Read%20Alignment%20%5BQWHLHF2Y%5D/reading-note.md)  线性参考比对快但有参考偏倚，全量图比对能缓解偏倚却计算昂贵。DCSMAP 利用线性比对特征，通过 XGBoost 筛选约 15% 的 read pairs 送入个性化泛基因组重比对，并通过局部 indel 重比对整合结果，将昂贵计算集中于可疑 reads，兼顾准确性与效率。

## Structural Variant callers

## Structural Variant genotypers



