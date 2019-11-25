## week9 作业

> ### __原图1__  

![picture1](https://github.com/lhz837540397/homework/blob/master/picture1.jpg)

> ### __复刻图1__ 

![remake1](https://github.com/lhz837540397/homework/blob/master/remake1.jpeg)

> ### __原图2__ 

![picture2](https://github.com/lhz837540397/homework/blob/master/picture2.jpg)

> ### __复刻图2__

![remake2](https://github.com/lhz837540397/homework/blob/master/remake2.jpeg)

> __复刻图1的实现代码__  

p + geom_col(width = 0.7) 

+scale_y_continuous(breaks = seq(-10, 25, 5), limits = c(-10, 25)) 

+geom_text(aes(label = `growth-rate`), vjust = -0.5) 

+ ylab("同比增长率/%") + xlab(NULL) 

+ scale_fill_manual(values = c('#2ec7c9','#b6a2de','#5ab1ef','#ffb980','#d87a80','#8d98b3','#e5cf0d','#97b552','#95706d','#dc69aa'),guide = FALSE) 

+ ggtitle('2018年我国主要再生资源类别回收量同比增长情况') 

+ theme(plot.title = element_text(hjust = 0.5, colour = '#5ab1ef', face ='bold'),axis.title.y = element_text(face = 'bold'),axis.line = element_line(size = 0.5, color = '#40828a'), axis.text.x = element_text(face = 'bold')) 

+ geom_hline(yintercept = 0,size = 0.5, color = "#40828a") 

+ theme(axis.line.x = element_blank(), panel.background = element_blank(), panel.grid.major.y = element_line(color = "#40828a",size = 0.5))

> __复刻图2的实现代码__
