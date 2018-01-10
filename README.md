# BUSINESS_MINERIA
MINERIA DE DATOS
install.packages("Rcpp")
library(readxl)
#se estableceeldirectorio de trabajo
WD <- "E:/rstudio/"
setwd( WD )
#se guardan el dataset en elobjeto banco
banco <- read.table("bancos.csv",sep=";", header = TRUE, fill = TRUE)
head(banco)
#consultamos algunos datos
#consultamos que tipos de datos tenemos
class(banco)
#consultamos los nombres que integran nuestra base de datos
names(banco)
#consultamos la tabla
head(banco)
#consultamos la nombre de filas
ls(banco)
#hacemos un resumen
summary(banco)
#consultamos los registros y atributos
print("Numero de Filas:")
nrow(banco)
print("Numero de columnas:")
ncol(banco)
#tipo de datos de cada columna
print("1. edad:")
class(banco$age)
#estadisticos descriptivos
summary(banco$age)#minimo,primer cuartil,mediana,media,tercercuartil,maximo
sd(banco$age)#desviacion estandar
edad<-banco$age
hist(edad,xlab = "Edades" ,ylab = "Frecuencias")#histograma
boxplot(edad,ylab="edades")#caja de cuartiles
#analisis de tipos de educacion de los clientes
levels(banco$education)
levels(banco$marital)
summary(banco$education)
barplot(summary(banco$education))
#analisis de lostipos de profesiones
profesiones<-levels(banco$job)
#se guardara en cantidad, la cantidad de clientes por profesion
cantidad<-summary(banco$job)
#creamos data un DTprof indicando las clientes de acuerdoa su profesion
DTprof<-data.frame(cantidad,profesiones)
#graficamos en el eje x las edades y en el eje y van automaticamente lasprofesiones
boxplot(banco$age~banco$job, ylab="edades", main="DistribuciÃ³n de edades por profesiÃ³n")
or <- DTprof[order(DTprof[,1],decreasing=FALSE),][,1]
