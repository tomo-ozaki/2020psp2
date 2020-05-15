# 課題5 レポート

aa83988848 薗田光太郎

## 課題

工学部20代の男性の身長は女性の身長より大きいと言えるか．男性と女性の平均身長が同じである蓋然性はどのくらいか．男性と女性の平均身長が同じとみなされるときに，標本男性の平均値と標本女性の平均値の差はどの範囲か．工学部20代の男性と女性の身長の分散は等しいとする．

等分散の2標本の平均の差の検定はt検定でおこなえる（調べてプログラムを書け）

## ソースコードの説明

## 入出力結果

```{R}
(u = ((length(data.male)-1)*var(data.male)+(length(data.female)-1)*var(data.female))/(length(data.male)+length(data.female)-2))
[1] 34.2765
> (se=sqrt(s/length(data.male)+s/length(data.female)))
[1] 3.161853
> (t=(mean(data.male)-mean(data.female))/se)
[1] 4.296136
> t.test(data.male,data.female,var.equal=T,alternative="greater")

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

棄却域は，R=[t12(0.05), inf) = [1.7823, inf)

母平均の差がないとすると，t=4.2961で，t\in R．p(T>t)=0.0005195
p<0.05 だし，p<0.01なので母平均の差がないという仮説は棄却される．つまり有意差がある．

今回の標本平均の差は，13.5837だが，ここから予想される母平均の差の95%信頼区間は 7.948419 < \mu1-\mu2 < Inf 
差が無いという0は100回中95回起きない．

棄却されないとき，
t < t12(0.05)
aveM-aveF < t12(0.05)*se = 

## 修正履歴

