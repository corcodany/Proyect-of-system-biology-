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

El paso a comenzar es generar un sistema sin tomar en cuenta la etapa de vida de los insectos y simplemente generar un sistema con dos variables.

## Probar libreria en Rstudio
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
