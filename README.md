# practica_series
##importar
library (foreign)
sd <- read.dbf("C:\\Users\\SALA-C17\\Downloads\\SDEMT215.dbf")
table(sd$CD_A)
table(sdo$CLASE1)


sd$R_DEF1 <- as.numeric(as.character (sd$R_DEF))
sd$C_RES1 <- as.numeric(as.character (sd$C_RES))
sd$EDA1 <- as.numeric(as.character (sd$EDA))

precod<-subset(sd, ((R_DEF1==0) & (C_RES1==1 | C_RES1==3) & (EDA1>=15 & EDA1<=98)), select = c(EDA1, SEX, HRSOCUP, CLASE2, CLASE1, CLASE3)) ##NUEVA BASE CON SEIS VARIALES
table (precod$R_DEF1)
table (precod$C_RES1)
table (precod$EDA1)
attach(precod)
CLASE2v1 <- table(CLASE2)
CLASE2v1
hist(CLASE2, )
hist(CLASE2, main = "Grafica 1. Distribucion de a poblacion de 15 años o mas,2015", 
     xlab = "Tipo de ocupada", ylab = "Poblacion (miles)",
     xlim = c(0,5), ylim = c(0, 200000), 
     border = T , pch = 18,
     col = c("violet", "turquoise4", "violetred1", "violetred2"))

CLASE2v<-as.numeric(as.character(CLASE2))
sd1<-subset(sociodemo, CLASE2 == 1, select = c(EDA,HRSOCUP, CLASE2,CLASE1,CLASE3,EDA5C,IMSSISSSTE))
frec<-table(sd1$IMSSISSSTE)

##labels le ponemos la etiqueta al vector
pie(frec, labels = c("Imss", "Issste", "Otra","No recibe", "No especificado"))

##para poner titulo
pie(frec, labels = c("Imss", "Issste", "Otra","No recibe", "No especificado"), main = "Institución de atención médica")

#col para poner color a cada sector
pie(frec, labels = c("Imss", "Issste", "Otra","No recibe", "No especificado"), main = "Institución de atención médica", col = c("green", "blue","red","turquoise4","gray"))


##graficas de barras
frec1<-table(sd1$EDA5C)
#View (frec1)
barplot(frec1)
#ponemos titulo
barplot(frec1,main = "Cinco grupos de edad")
#ponemos color
barplot(frec1,main = "Cinco grupos de edad", col = c("brown", "blue","red","turquoise4","gray"))
#etiquetas se pueden poner con names.arg
barplot(frec1,main = "Grafica1. Cinco grupos de edad", col = c("brown", "blue","red","turquoise4","gray"), names.arg = c("menor","14 a 24", "25 a 44", "45 a 64", "65 y más" , "n.e"), ylim = c(0,85000))

names(frec1)<- c("menor","14 a 24", "25 a 44", "45 a 64", "65 y más" , "n.e")
barplot(frec1,main = "Cinco grupos de edad", col = c("blue","red","turquoise4","gray", "brown"), xlab = "Edad", ylab = "Poblacion")

