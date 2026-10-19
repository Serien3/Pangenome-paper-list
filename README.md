## Preface

本仓库记录关于 Pangenome 的文章。看过的文章会至少用一句话概括内容，有些还会有 notes 。只有标题的就是还没看过的，只是先存档到这里。

### 🔥 Updates

- 2026-10 接下来主要关注泛基因组构建,以及泛基因组数据结构的相关工作

## Directory

⭐ 表示文章较多；🔥表示当前主要关注并更新

- ⭐🔥[Pangenome construction](#pangenome-construction)
- [Annotating pangenomes](#annotating-pangenomes)
- [Structural Variant callers](#structural-variant-callers)


# Pangenome

## Pangenome construction

1. [Genome Biology]**The design and construction of reference pangenome graphs with minigraph**[[paper]](https://doi.org/10.1186/s13059-020-02168-z) [[Github]](https://github.com/lh3/minigraph)[[reading-note]](The%20design%20and%20construction%20of%20reference%20pangenome%20graphs%20with%20minigraph%20%5BR642E5L5%5D/reading-note.md)  minigraph 用 minimizer 种子 + 两级 chaining（段内线性链 DP 配 100kb 大 gap 罚分和 RMQ 混合加速，链间靠"最短 16 条游走中长度最接近查询间距"消歧选路）做无碱基比对的序列到图定位，再对链上锚点空隙打分（η·max gap）用 Ruzzo-Tompa 提候选分歧区、局部 pairwise 比对验证 ≥100bp INDEL 或 <80% 一致性后增广，从而在不用未实现的碱基级环图比对的前提下增量构造全基因组参考图。

## Annotating pangenomes

## read alignment to a pangenome graph

## Structural Variant callers

## Structural Variant genotypers



