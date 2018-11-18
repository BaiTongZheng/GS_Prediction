2018/11/14
改进思路：
1.新加的一些特征比较重要：例如会话质量，会话时间。
2.适当增加训练集的大小，不仅仅只取2017年5-10月作为训练集
3.增加一些可以表示客户访问频率的指标，很显然，频率越高则用户未来会访商店的概率越高。

特征分析：

提取斜杠深度：
'hits_appInfo.exitScreenName' 
'hits_appInfo.landingScreenName' 
'hits_page.pagePath'
hits_page.pagePathLevel1
hits_page.pagePathLevel2
'hits_page.pagePathLevel3'
'hits_page.pagePathLevel4'
                           hits_referer
trafficSource_referralPath
