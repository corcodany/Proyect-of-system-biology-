# Proyect-of-system-biology
## Definicion de tema 10-01-22
### Idea de articulos sobre Sistemas Lotka-Volterra
Se eligio el tema sobre Sistemas de Lotka-Volterra para generar una red de interacción depredador-presa y como la alteración de alguna de las partes genera cambios en la red.
Queda pendiente escoger las especies que van a interactuar y el como.


SISTEMAS DINÁMICOS. APLICACIONES A LAS REDES COMPLEJAS.
ANALISIS CUALITATIVO DE SISTEMAS DE ECUACIONES DIFERENCIALES. APLICACIONES A MODELOS DE LOTKA-VOLTERRA N-DIMENSIONALES

Structural identifiability of the generalized Lotka–Volterra model for microbiome studies https://royalsocietypublishing.org/doi/full/10.1098/rsos.201378

## ¿Qué tipo de proyecto puede generarse con redes biologicas? 17-01-22
Se pretende utilizar el sistema Lotka Volterra para generar y comprender una red biologica con autorregulaciones y sus caracteristicas.

## Generación sistema Lotka-Volterra en PHYTON ó RStudio 24-01-22
### Ejemplos de sistema con la ecuación 
https://scientific-python.readthedocs.io/en/latest/notebooks_rst/3_Ordinary_Differential_Equations/02_Examples/Lotka_Volterra_model.html
https://aubreymoore.github.io/ALBI345F17/pdfs/Lotka-Volterra-Model.html

## Idea de inicio del sistema simulado 31-01-22
Se me ocurre idear un sistema tipo Lotka Volterra, en el caso de un sistema de control de plagas y como la ocilación entre cantidad de plaga e insectos control interfiere entre la interacción. En el caso de las catarinas (Coccinellidae), que en su etapa larvaria es cuando más insectos plaga deboran. En ese caso, ¿Como podria simularse las diferentes etapas de vida de los insectos plaga y los insectos control?, ¿Que tanta diferencia de control se tiene en cada etapa? y ¿Como se podria generar una red programada en phyton?.

https://doi.org/10.1111/1440-1703.12243

Kindlmann, P., Štipkova, Z., & Dixon, A. (2020). Generation time ratio, rather than voracity, determines population dynamics of insect–natural enemy systems, contrary to classical Lotka-Volterra models. European Journal of Environmental Sciences, 10(2), 133-140.

El paso a comenzar es generar un sistema sin tomar en cuenta la etapa de vida de los insectos y simplemente generar un sistema con dos variables.

## Probar libreria en Rstudio 7-02-22
 library(deSolve)

LotVmod <- function (Time, State, Pars) {
    with(as.list(c(State, Pars)), {
        dx = x*(alpha - beta*y)
        dy = -y*(gamma - delta*x)
        return(list(c(dx, dy)))
    })
}

Pars <- c(alpha = 2, beta = .5, gamma = .2, delta = .6)
State <- c(x = 10, y = 10)
Time <- seq(0, 100, by = 1)

out <- as.data.frame(ode(func = LotVmod, y = State, parms = Pars, times = Time))

matplot(out[,-1], type = "l", xlab = "time", ylab = "population")
legend("topright", c("Cute bunnies", "Rabid foxes"), lty = c(1,2), col = c(1,2), box.lwd = 0)

## Mejorar la libreria en Rstudio 21-02-22
Utilizaré esta documentación de R para mejorar el script, ya que es para ecucaciones diferenciales, y Lotka-Voleterra funciona con ecuaciones diferenciales
https://desolve.r-forge.r-project.org/

## Rstudio no ha funcionado, se intentara llevar el proceso a phyton 7-03-22
Se utilizará esta página como refencia, cambiando las variables y el tipo de interacción.
Esta libreria en github explica mejor(https://github.com/smkalami/lotka-volterra-in-python) asi que, intentare complementar el codigo para metenerle mas variables y los valores.

## Usar estos articulos como refencia 14-03-22
https://www.sciencedirect.com/science/article/pii/S0021782418300898



Video que explica mejor las funciones de python https://youtu.be/2f5aRTBmm10 

## Agregar una interacción mas con los resultados de la primer interacción

## Entender las ecuaciones diferenciales y el modelo de Runge-Kutta 04-04-22 
https://relopezbriega.github.io/blog/2016/01/10/ecuaciones-diferenciales-con-python/
https://www.sciencedirect.com/topics/mathematics/runge-kutta-method

## Agregar una tercera especie 18-04-22
http://blog.espol.edu.ec/analisisnumerico/sistemas-edo-modelo-predador-presa/
https://matplotlib.org/2.2.5/tutorials/index.html para poder graficar correctamente

https://jrbp.stanford.edu/research/publications/gilbreath-susan-1998-lotka-volterra-equation-cladocerans-multiple-species Este articulo habla de Lotka-volterra con varias especies.

## Modificar los parametros de la interacción para la tercer especie.
https://doi.org/10.1016/j.amc.2013.08.093 

## La tercer especie ya esta añadida en la ecuación y en las variables, ahora hay que graficar para tener una grafica de interacción.
https://jakevdp.github.io/PythonDataScienceHandbook/04.12-three-dimensional-plotting.html

## Modificar el tamaño de población inicial para ver los posibles resultados
