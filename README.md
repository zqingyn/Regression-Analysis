---
title: "回归分析实验1"
author: "zq"
format: html
editor: visual
---

## 1、数据的导入

模拟生成所需要的数据：下列代码能生成两个模拟数据集tempdata.csv和tempdata.xlsx.

```{r}
n=20
p=5
dt=matrix(rnorm(n*p),n,p)
dt=as.data.frame(dt)
names(dt)=c('x1','x2','x3','x4','x5')
dt$y=0.5+dt$x1+2*dt$x2+3*dt$x3+4*dt$x4+5*dt$x5+rnorm(n)
dt
write.csv(dt,'tempdata.csv')
openxlsx::write.xlsx(dt,'tempdata.xlsx')
```


### 1. 结构化数据导入

#### 1.1 文本格式
- 1、read.table
- 2、read.csv
```{r}
#用read.table导入csv文件
dt1 = read.table('tempdata.csv',sep=',',header = T)
head(dt1)

#用read.table导入csv文件
dt2 = read.csv('tempdata.csv',header = T)
head(dt2)
```

#### 1.2 excel格式数据

- 1、用openxlsx::read.xlsx导入xlsx文件
- 2、用readxl::read.excel导入xlsx文件
```{r}
#用openxlsx::read.xlsx导入xlsx文件
dt3=openxlsx::read.xlsx('tempdata.xlsx')
head(dt3)

#用readxl::read.excel导入xlsx文件
dt4=readxl::read_xlsx('tempdata.xlsx')
head(dt4)
```

#### 1.3 导入其他软件数据（比如spss,sas,stat)

- foreign::read.spss(spss格式)
- foreign::read.ssd（sas格式）
- foreign::read.dta（stat格式）
