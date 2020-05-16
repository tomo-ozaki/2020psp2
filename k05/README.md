# 課題5 レポート

aa83988848 薗田光太郎

## 課題

工学部20代の男性の身長は女性の身長より大きいと言えるか．男性と女性の平均身長が同じである蓋然性はどのくらいか．男性と女性の平均身長が同じとみなされるときに，標本男性の平均値と標本女性の平均値の差はどの範囲か．工学部20代の男性と女性の身長の分散は等しいとする．

等分散の2標本の平均の差の検定はt検定でおこなえる（調べてプログラムを書け）

## ソースコードの説明

## 入出力結果

```
data.male = c(183.87,
179.54,
173.62,
167.83,
174.38,
171.38,
169.39,
171.10)
data.female = c(166.90,
165.62,
152.40,
163.24,
161.39,
152.28)
```

```
mu = 0
conf.level = 0.95
nx = length(data.male)
ny = length(data.female)
mx = mean(data.male)
my = mean(data.female)
ux = var(data.male)
uy = var(data.female)
df = nx+ny-2
(u = ((nx-1)*ux+(ny-1)*uy)/df)
```
[1] 34.2765
```
(stderr=sqrt(u/nx+u/ny))
```
[1] 3.161853
```
(tstat=(mx-my-mu)/stderr)
```
[1] 4.296136
```
pval = pt(tstat, df, lower.tail = F)
cint = c(tstat - qt(conf.level, df), Inf)
cint <- mu + cint * stderr
```

```
t.test(data.male,data.female,var.equal=T,alternative="greater")
```

```
	Two Sample t-test

data:  data.male and data.female
t = 4.2961, df = 12, p-value = 0.0005195
alternative hypothesis: true difference in means is greater than 0
95 percent confidence interval:
 7.948419      Inf
sample estimates:
mean of x mean of y 
 173.8887  160.3050 
```
varは不偏分散

母平均の差がないとすると，t=4.2961で，p(T>t)=0.0005195

母平均の差の95%信頼区間は 7.948419 < \mu1-\mu2 < Inf 

## 修正履歴

