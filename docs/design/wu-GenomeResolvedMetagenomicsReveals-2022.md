 ## 方法
- 一个农业点，两个恢复林地点R40/R10。小麦-玉米轮作，不施肥CK，化肥CF，化肥+有机肥CFM。共5种处理6次重复
- NH<sub>4</sub><sup>+</sup>-N / NO<sub>3</sub><sup>-</sup>-N / AP / AK / SOC / TN
- 16S  505F/909R, ITS。OTU丰度通过edgeR进行差异分析，用adopted indicator species寻找组间普遍存在的差异OTU。
- 宏基因组丰度做了稀释。收集13、52的文献和K00117， **interProScan**区分并排除可溶性磷酸盐，功能基因丰度做z-score转化。
- metaWrap做binning，checkm评估完整度超过70%，污染度低于10%。GTDB-TK做物种分类
- 用120个农业土(玉米)和72个森林土测序结果(文献61,62)做meta分析