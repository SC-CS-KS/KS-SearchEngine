# 评估


## 指标
```md
TP —— True Positive （真正, TP）被模型预测为正的正样本；可以称作判断为真的正确率
TN —— True Negative（真负 , TN）被模型预测为负的负样本 ；可以称作判断为假的正确率
FP ——False Positive （假正, FP）被模型预测为正的负样本；可以称作误报率
FN——False Negative（假负 , FN）被模型预测为负的正样本；可以称作漏报率
True Positive Rate（真正率 , TPR）或灵敏度（sensitivity） 
　　TPR = TP /（TP + FN） 
　　被预测为正的正样本结果数 / 正样本实际数
True Negative Rate（真负率 , TNR）或特指度（specificity） 
　　TNR = TN /（TN + FP） 
　　被预测为负的负样本结果数 / 负样本实际数
False Positive Rate （假正率, FPR） 
　　FPR = FP /（TN + FP） 
　　被预测为正的负样本结果数 /负样本实际数
False Negative Rate（假负率 , FNR） 
　　FNR = FN /（TP + FN） 
　　被预测为负的正样本结果数 / 正样本实际数
```

* 准确率 （Precise）
```md
在所有的数据中，机器预测正确的占比；换句话说，对所有数据来说，机器对了多少？
```
* 召回率 （Recall）
```md
是检索出的相关文档数和文档库中所有的相关文档数的比率，衡量的是检索系统的查全率。
在所有准确的数据中，机器预测正确的占比；换句话说，对应该对的数据来说，机器找到了多少个对的？
```
