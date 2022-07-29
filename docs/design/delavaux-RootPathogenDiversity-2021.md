## 取样
成对或集群取样，自然14sites，扰动12sites。每点四个plots，每个plot四象限法混样。
[[202204061112#Fig1]]
真菌用ITS7和ITS4扩增，卵菌用ITS3oo和ITS4扩增。qiime1处理，UNITE ITS数据库注释，去掉总和小于5的OTU，DESeq2标准化。用FUNGuild数据库挑选出真菌中的病原真菌，同时挑选出腐生真菌，将腐生真菌与病原真菌的分析结果进行比较。BLAST比对NCBI卵菌ITS2序列，但是有偏好，所以放在附图附表中。

pez包提取PSR值。通过GLM和PERMANOVA计算扰动、温度、降水（以及其他土壤因素）与系统发育物种丰度的影响（PSR）。通过Venn图和DESeq2评估差异。
