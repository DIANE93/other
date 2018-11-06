# magrittr
library(magrittr)
#by()分组后对各组进行回归
#by(R,R$class,function(m)lm(m[,2]~m[,3]))
set.seed(12)
class<-rbinom(10000,1,0.5)#产生伯努利随机数
x1<-c(rep(1,10000))
x2<-rnorm(10000)
x<-cbind(x1,x2)
theta.tru<-c(1,1)
lamda.tru<-exp(x%*%theta.tru)
y<-rpois(10000,lamda.tru) #按lamda.tru的泊松分布产生10000个随机数
R<-data.frame(class,x2,y)
by(R,R$class,function(m)lm(m[,2]~m[,3]))#分组回归

#%>% 向右操作符(forward-pipe operator)
set.seed(12)
class<-rbinom(10000,1,0.5)
rnorm(10)%>%
  cbind(c(rep(1,10)))%>%
  '%*%'(c(1,1))%>%
  exp%>%
  rpois(10)%>%
  y<-
R<-data.frame(class,rnorm(10),y)
by(R,R$class,function(m)lm(m[,2]~m[,3]))#分组回归
  ##data.frame(class,rnorm(10))%>%
  #R<-%>%print(R)
  #R
  
