# Exploracion-de-datos-hidrologicos

inp <- read.csv("FDC.csv", na.strings ="")


head(inp)
dim(inp)






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

summary(inp[,2:3])
