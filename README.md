# Exploracion de datos hidrologicos

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
  
  ### Para poder observar (en RStudio) los datos de manera resumida, a través de un promedio estadístico, de ambos ríos, se deberá escribir la siguiente función.

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

