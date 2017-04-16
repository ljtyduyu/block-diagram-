# block-diagram-
##use block diagram  to  compare  order！


```r
library(ggplot2)
library(ggmap)
```

```r
mydata<-data.frame(X=c(3,7,11,15,19),A=c(2471,1893,1248,1078,556),B=c(1385,951,869,784,366),C=c(56,7,19,13,40))
mydata$Axmin<-mydata$X-sqrt(mydata$A)/30
mydata$Axmax<-mydata$X+sqrt(mydata$A)/30
mydata$Aymin<-0
mydata$Aymax<-sqrt(mydata$A)/15

mydata$Bxmin<-mydata$X+sqrt(mydata$A)/30-sqrt(mydata$B)/15
mydata$Bxmax<-mydata$X+sqrt(mydata$A)/30
mydata$Bymin<-0
mydata$Bymax<-sqrt(mydata$B)/15


mydata$Cxmin<-mydata$X+sqrt(mydata$A)/30-sqrt(mydata$C)/10
mydata$Cxmax<-mydata$X+sqrt(mydata$A)/30
mydata$Cymin<-0
mydata$Cymax<-sqrt(mydata$C)/10

mydata$text<-c("University of\n Pennsylvania","University of\n Notre Dame","Princeton\n University","Stanford\n University","California Institute\n of Technology")
mydata$full<-c("31663","16548","27189","34348","5225")
```


```r
windowsFonts(myFont = windowsFont("arial"))
ggplot(mydata)+
geom_rect(aes(xmin=Axmin,xmax=Axmax,ymin=Aymin,ymax=Aymax),fill="#59AF8A")+
geom_rect(aes(xmin=Bxmin,xmax=Bxmax,ymin=Bymin,ymax=Bymax),fill="#0074A3")+
geom_rect(aes(xmin=Cxmin,xmax=Cxmax,ymin=Cymin,ymax=Cymax),fill="#C72733")+
geom_linerange(aes(x=X+2,ymin=0,ymax=4.8),col="grey",linetype=2)+
ylim(-.5,6)+
labs(x="",y="")+
geom_text(aes(x=X,y=4.5,label=text),size=4,fontface="bold",family="myFont")+
geom_label(aes(x=X,y=3.7,label=full),fill="#EFE5CA",colour="black",fontface="bold",size=3.5,label.r=unit(0.15,"lines"),family="myFont")+
geom_text(aes(x=Axmin,y=Aymax,label=A),hjust=-.2,vjust=1,size=3.5,col="white",family="myFont")+
geom_text(aes(x=Bxmin,y=Bymax,label=B),hjust=-.2,vjust=1,size=3.5,col="white",family="myFont")+
geom_text(aes(x=Cxmin,y=Cymax,label=C),hjust=-.2,vjust=1,size=3,col="white",family="myFont")+
annotate("text",x=2.5,y=5.7,label="Class Struggle",col="black", size=6,family="myFont")+  
annotate("text",x=8.85,y=5.2,label="A spot on a university or college's waitlist rarely translates into admission. A look at the numbers for several institutions", size=4,family="myFont")+  
annotate("text",x=3.9,y=-.32,label="Source:The universities and 2011-2012 Common Data Set",col="black",size=3,family="myFont")+  
annotate("text",x=19.8,y=-.32,label="The wall Street Jaunual",col="black",size=3,family="myFont")+  
theme_nothing()+
theme(panel.background=element_rect(fill="#F5F2E1"))
```

```r
### 建议保存尺寸（1035*330） <br>
mydata1<-mydata[,5:8]
names(mydata1)<-c("xmin","xmax","ymin","ymax")
mydata1$Group<-"A"

mydata2<-mydata[,9:12]
names(mydata2)<-c("xmin","xmax","ymin","ymax")
mydata2$Group<-"B"

mydata3<-mydata[,13:16]
names(mydata3)<-c("xmin","xmax","ymin","ymax")
mydata3$Group<-"C"

mynewdata<-rbind(mydata1,mydata2,mydata3)
mynewdata$Group<-factor(mynewdata$Group,order=T)

ggplot(mynewdata)+
geom_rect(aes(xmin=xmin,xmax=xmax,ymin=ymin,ymax=ymax,fill=Group))+
scale_fill_manual(values=c("#59AF8A","#0074A3","#C72733"))
```

联系方式：
----------------------------------------------------
wechat：ljty1991  <br>
Mail:578708965@qq.com <br>
个人公众号：数据小魔方（datamofang） <br>
团队公众号：EasyCharts <br>
qq交流群：[魔方学院]553270834

个人简介：
-------------------------------------------------
**杜雨** <br>
财经专业研究僧； <br>
伪数据可视化达人； <br>
文科背景的编程小白； <br>
喜欢研究商务图表与地理信息数据可视化，爱倒腾PowerBI、SAP DashBoard、Tableau、R ggplot2、Think-cell chart等诸如此类的数据可视化软件，创建并运营微信公众号“数据小魔方”。 <br>
Mail:578708965@qq.com <br>
![resume](https://github.com/ljtyduyu/FontMap-of-China/blob/master/Image/resume.png)

友情推荐：
-------------------------------------------
**周闻文**：Python爬虫大神，各种炫酷高能手法玩出爬虫新境界！！！<br>
#### 简书主页：[duohappy](http://www.jianshu.com/u/5a8f3b911f56)


备注信息：
----------------------------------------------------
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />本作品采用<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">知识共享署名-非商业性使用 4.0 国际许可协议</a>进行许可。

