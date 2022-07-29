#phyloseq
## 需要文件
1. 进化树对象，phylofactor
2. otu表，vector/matrix/data.frame
3. 分类信息（可选），data.frame, 第一列与进化树一致， 第二列是分号分隔的物种信息
4. meta信息, data.frame

## 导入原始数据
```
library(phylofactor)
library(phyloseq)
library(dplyr)

physeq <- import_qiime("otu.csv", "meta.txt", verbose=TRUE)  # 注意OTU表最后一列的列名叫"Consensus Lineage"
mytree <- phy_tree(read.tree("../rawdata//ASV_phylo.tre"))
physeq <- merge_phyloseq(physeq, mytree)

```

## 计算pH相关因子

```
profile <- physeq %>% otu_table %>% data.frame
tree <- physeq %>% phy_tree
meta <- physeq %>% sample_data %>% data.frame
pf_PhyloFactor <- PhyloFactor(profile, tree, meta, frmla = Data~pH, stop.early=TRUE, choice="F")
```
## 一个不太漂亮的图
```
factor_sele <- c(1:pf_PhyloFactor$nfactors)[pf_PhyloFactor$factors$Group1 != "tip"]
pf.heatmap(pf_PhyloFactor,factors=factor_sele,
column.order=order(pf_PhyloFactor$X$pH),
width=3) + 
ggtree::geom_tiplab()
```
## 看物种分类
```
for(i in factor_sele){
    asv_i <- pf_PhyloFactor$groups[[i]]$Group1
    asv_n <- tree$tip.label[asv_i]
    physeq %>% tax_table %>% .[asv_n, 3:7] %>% print
}
```
