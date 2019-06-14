# R 学习笔记

标签（空格分隔）： 统计

---

### 文档相关

1、 读取csv `read.csv('gplay_app.csv')` 数据导出 `write.csv(result,"sample2.csv", na="NA")`

### 相关性分析

1、 安装 corrplot `install.packages("corrplot")` 加载包`library("corrplot")`

2、 计算相关性分析 `cor(data)`  `cor(data, method = "spearman")` `cor(data, method = "kendall")`

3、 画图 `corrplot(the_result_of_corData, method = "null/pie/color"， addCoef.col="word_color")` method分别是点图，饼图， 像马赛克的。 addCoef.col设置显示向关系的颜色。

### ggplot2
library(ggplot2) 加载
1、`ggplot(pg_mean, aes(x=group, y=weight)) + geom_bar(stat="identity")` 绘制直方图
2、`ggplot(pg_mean, aes(x=factor(group), y=weight)) + geom_bar(stat="identity")`变量进行因子转化
3、`geom_bar(stat="identity", fill="lightblue", colour="black")` 赋予颜色，fill填充颜色， color 是线条颜色
4、


### 杂项 
1、 读取工作目录 `getwd()` 设置工作目录 `setwd()`
2、 apply 函数 `apply(x,1,sum)` 对一个矩阵x的每一行求和。 `apply(x,2,sum)` 对一个矩阵x的每一列求和
3、 取消科学计数法 `options(scipen=200)`
4、 cbind 合并两个向量
5、 `aggregate(x=data], by = list(salarys$SEX), FUN=max)` 分组统计



