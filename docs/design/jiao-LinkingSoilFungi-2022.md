## 实地调查
### 取样
2017年7-8月取样，126个点，每个点3个plots，分为深层(15-30cm)和浅层(0-15cm)。包含37个农业，28个森林，15个湿地，26个草地，20个沙漠。沿河西走廊。一个沙漠表层样品DNA提取失败，共251个样品。

### 土壤性质
* 常规指标：pH, moisture, cation exchange capacity(CEC)阳离子交换量, SOC, DOC, TN, NO<sub>3</sub>, NH<sub>4</sub>, TP, AP, TK, AK.
* 气候数据：来自[Worldclim database](www.worldclim.org).
* 干旱指数(AI): 1-降水/蒸发量，来自**Global Potential Evapotranspiration database**.

### 测序
* 细菌16S v4-v5区
* 真菌18S ITS1 

## Microcosm study
土壤来自于中国西北的干旱区，2019年8月取aridity=0.663草地，0-15cm表层土。土样过2mm筛，气候室25℃平衡数周。然后移至塑料盆，用杀菌剂(环乙酰亚胺)修正，**三个梯度0(D0)，6ppm(D1)，14ppm(D2)，四个重复**，共12个样品。20℃培养60天。

## 分析
### Spatial mapping of bacterial diversity
预测细菌Shannon多样性，co-kriging interpolation(automap), 5个环境指标：soil properties(soil C and pH), climate(AI and MAT). Cross-validation 基于pearson相关系数（automap::autoKrige.cv）。
土壤属性来自[ISRIC](https://soilgrids.org/#!/?layer=geonode:taxnwrb_250m)(global gridded soil information) Soil Grids.
### Correlation Network
超过10%样品中出现的ASV，|Spearman's *p*| > 0.6 & p < 0.001
### DDRs
1-bray_curtis
### Null model
βNTI，Stegen的过程。
### Statistical
随机森林(rfPermute)，多元线性回归(stats::lm)，方差分解(relaimpo::calc.relimp)，基于R<sup>2</sup>的前向选择(vegan::ordiR2step)，CAP(vegan::capscale), standard/partial Mantel test(ecodist::mantel)，NMDS(vegan::metaMDS)。
