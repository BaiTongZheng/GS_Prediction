2018/10/24

test : 1.709925685736863
submisson :1.4453

分析：

	1.在chanelGroup等字符串类型的编码方式为LableEncode,每个类别所得到的编码值为0,1,2,3,4,5,6,7，用户访问商店的渠道之间应该是相互独立的，如果采用线性分类器，相当于默认编码值与收入正相关或负相关。	
		可以考虑修改为独热向量（one-hot）
	2."trafficSource.adwordsClickInfo.page", 
      "trafficSource.adwordsClickInfo.slot"
	  这两个属性的特征权重非常小（2），可以考虑直接去除
	3.原模型中totals.pageviews，totals.newVisits，totals.bounces 存在缺失值。
	  其中totals.pageviews是非常重要的特征（981），totals.newVisits（91），totals.bounces（86）

试验记录：

	1.去除chanelGroup属性
	test :1.7125884083540919 
	submisson :1.4455
	结论：单纯去除该属性的话在测试集上和提交检验效果上略微变差。
    chanelGroup属性的权重略高(137)，但是实际影响偏低

	2.去除"trafficSource.adwordsClickInfo.page", "trafficSource.adwordsClickInfo.slot"两个属性
	test:1.7094664132699176
    submisson:  1.4473
	结论：这两个权重只有2，但是要比chanelGroup（137）还重要。
    
问题：
	1.lightgbm回归属于非线性方式还是线性方式？
	lightgbm会对分类特征的属性值进行重新排序。

资料：
	lightgbm不需要进行one-hot-encode。

	https://cdn2.jianshu.io/p/ba9ab1adbfe1
	http://lightgbm.apachecn.org/cn/latest/Quick-Start.html







