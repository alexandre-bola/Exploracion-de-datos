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
