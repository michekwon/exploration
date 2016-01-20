X = function(A=1,B=-2,C=-1.5,D=-3,n=1000)
{
  dt = 1/n
  dX = (A + B*(1:n)*dt)*dt + exp( C + D*(1:n)*dt ) * sqrt(dt) * rnorm(n)
  return( cumsum(dX) )
}
library("graphics")
clr = rainbow(100)
plot(X(),type='l',xlab="t",ylim=c(-0.2,0.5),main="R plots in documents are amazing!")
H = matrix( nrow = 100 , ncol = 1000 )
for( i in 1:100 ){ H[i,] = X() }
idx = sort(H[,1000],index.return=T)
H = H[ idx$ix , ]
for( i in 1:100 )
  {lines( H[i,] , type='l' , col=clr[i] )}