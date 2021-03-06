# Exploración de datos hidrologicos
## Procesamiento de Datos Geográficos
## Alexandre Bolaños Umaña

### Para poder iniciar, debemos cargar y leer el archivo csv en cuestión, así podremos trabajarlo, para ello utilizaremos las siguientes funciones:
inp <- read.csv("FDC.csv", na.strings ="")


### Para poder observar los encabezados, así como sus dimensiones, escribiremos lo siguiente:

head(inp)
dim(inp)





### Seguidamente, para poder observar los datos graficados, así como para asignarle un color en el gráfico, se deberá escribir la siguiente función:
plot(
  inp[,2], type = "l", col="blue", 
  main = "Volmen del agua",
  xlab = "Fecha",
  ylab = "Caudal en mm"
)
lines(inp[,3], col="red")

legend(
  x = "topleft",
  inset = 0.05,
  legend = c("Estrella", "Banano"),
  fill = c("blue", "red"),
  horiz = FALSE
  )![Graphic1](https://user-images.githubusercontent.com/82826151/119308878-d39f1a80-bc2a-11eb-89b9-3a7617bc06a8.png)
  
  ### Para poder observar (en RStudio) los datos de manera resumida, a través de un promedio estadístico, de ambos ríos, se deberá escribir la siguiente función:

summary(inp[,2:3])

### Para poder visualizar los datos en forma de histograma, se deberá poner la siguiente función:
summary(inp[,2:3])
hist(inp[,2],
main = "Estrella",
xlab = "Cantidad por dia en Mm",
ylab = "Regularidad", 
) 
![Graphic2](https://user-images.githubusercontent.com/82826151/119314971-9048aa00-bc32-11eb-8962-1f8bfbadaf64.png)

hist(inp[,3],
main = "Banano",
xlab = "Cantidad por dia en Mm",
ylab = "Regularidad",
)
![Graphic3](https://user-images.githubusercontent.com/82826151/119315353-fcc3a900-bc32-11eb-8e01-0dd0d67f66e6.png)

### Para ordenar de mejor manera la información, la siguiente función nos ayudará a evaluar datos en el archivo csv y poder observarlos y analizarlos de mejor manera:
names(inp) <- c("Fecha", "Estrella", "Banano")
attach(inp)
plot(Estrella,
main = "Rio Estrella", 
xlab = "Fecha",
ylab = "Caudal por dia en Mm",
)
![Graphic4](https://user-images.githubusercontent.com/82826151/119318394-7b6e1580-bc36-11eb-92c6-f0c4e34cfd95.png)
### Para poder definir el tiempo del archivo, debemos crear un archivo intermedio, el cual definirá (dentro del archivo, día, mes y año).
Tempdate <- strptime(inp[,1], format = "%d/%m/%Y") 

### Con la función anteriormente vista, se podrán poner fechas específicas, para periodos de tiempo anuales, se deberá utilizar la siguiente función:
MAQ_Estrella <- tapply(Estrella,
format(Tempdate, format = "%Y"),
FUN = sum)
MAQ_Banano <- tapply(Banano,
format(Tempdate, format = "%Y"), 
FUN = sum)
write.csv(rbind(MAQ_Estrella, MAQ_Banano),  file = "MAQ.csv")

### Para poder observar de manera graficada, lo anteriormente generado, debemos utilizar la siguiente función:

plot(
MAQ_Banano, ylim = c(0,3000),
main = "Valor en Mm por año",
xlab = "Fechas",
ylab = "Caudal anual",
)
lines(MAQ_Estrella, col = 2)
      
legend(x = "topright",
inset = 0.05,
legend = c("Estrella", "Banano"),
fill = c("red", "black"),
horiz = FALSE
)![Graphic5](https://user-images.githubusercontent.com/82826151/119325854-904ea700-bc3e-11eb-8501-8c8ccfa919da.png)

### Debemos utilizar nuevamente la función _"tapply"_, para realizar periodos mensuales.
MMQ_Estrella <- tapply(Estrella,
format(Tempdate, format = "%m"), 
FUN = sum)
MMQ_Banano <- tapply(Banano,
format(Tempdate, format = "%m"), 
FUN = sum)

### Utilizaremos la función _"cor"_ para poder obtener datos que muestran una correlación.
corinp <- cor(inp[,2:3], method = "spearman")

plot(Estrella, Banano,
     main = 'Correlacion de las cuencuas del Rio Banano y el Rio Estrella',
)
inp.lm <- lm(Estrella ~ Banano, data = inp)
summary(inp.lm)
![Graphic6](https://user-images.githubusercontent.com/82826151/119330669-b88cd480-bc43-11eb-869b-0a711af74e7d.png)

### Para finalizar, se visualizarán modelos analíticos para comparar y relacionar los residuos de ambos ríos. Para esto, usaremos la siguiente función: 
plot(inp.lm)
![Graphic7](https://user-images.githubusercontent.com/82826151/119331541-b414eb80-bc44-11eb-9b8c-9af4f50f0203.png)
![Graphic8](https://user-images.githubusercontent.com/82826151/119331778-fdfdd180-bc44-11eb-8178-8024d0a9d32d.png)
![Graphic9](https://user-images.githubusercontent.com/82826151/119331798-048c4900-bc45-11eb-9a13-36cab137ba27.png)

