---
layout: post
title:  "Steering Target"
date:   2020-05-26 23:59:35 -0400
categories: gamedev
---
Lamentablemente el Pathfinding no fue obra mia, y es un script que saque desde la unity asset store despues de muchos tutoriales fallidos que se iban hacia funciones que realmente no necesitaba. Aun asi me daria almenos un poco de credito para ajustarlo a mis necesidades lo cual costo un poco pero aun asi eso se eclipsa un tanto por la hermosa documentacion que tiene el dueño del asset, todos los script, cada funcion y variable explicada en su pagina y discutida en su foro, este Pathfinding es ciertamente de lo mejor que hay incluso en su version free, por principio lo comprare cuando pueda ya que aun asi la version pagada son 100 USD.

El pathfinding hace que los mounstros encuentren un camino entre los obstaculos hacia el player dividendo el mapa en nodos y dandoles un valor a cada ruta que lo lleve (y no lo lleve) mas cerca del player, la ruta mas barata sera la que el mounstro tomara, con mucho ensayo y error se logro aplicar a Danmakui perfectamente pero aun tenia un problema.
La animacion del mounstro estaba siempre mirando hacia el [Player] osea su localizacion final cuando, en general, creo yo, los seres vivos miran hacia donde se diriguen pero no necesariamente hacia su punto de destino final.

Intente buscar como hacer para que el mounstro registrara cual es el siguiente [Nodo] (las divisiones del mapa) por el que va a pasar y mirar hacia alli. 
Pero no existia una funcion rapida que hiciera eso pero encontre lo siguiente mejor.
el valor Vector3 [SteeringTarget] que se describe como "Un punto de la ruta que esta entre el [Agente] y el [Target] o que puede ser hasta el mismo target, el steering target es como el limite de vision que tiene el [Agente] Lo cual hace que funcione perfecto para lo que necesitaba.

El problema era que este valor es un Vector 3 y las animaciones del mounstro usan valores Transform para determinar hacia donde mira, realmente no voy a explicar que es Vector 3 o Transform especificamente, no por que sea complicado si no por que no se, y no lo le leido, sounds like some math sorcery shit to me.
El punto es que tampoco son convertibles el uno en el otro por que lidian con cosas distintas,  Localizaciones pero uno de estos es la localizacion global y el otro la localizacion local.

Me costo unas cuantas horas para rendirme en traducirlos y pasar por esto facilmente hasta que finalmente me puse a pensar debidamente.
Era una solucion que ya estaba aplicando en otro mounstro donde mounstros mas pequeños persiguen puntos invisibles que orbitan al mounstro mas grande
Entonces hice lo siguiente 
-El Script creara un objecto invisible [TargetFocus]
-La localizacion de [TargetFocus] sera la misma que la de Steering target y esto se actualizara cada frame por lo tanto siempre tendra la misma localizacion que steering target.
-Sacar transform de un objecto es lo natural, asi que convertir la localizacion de [TargetFocus] es el lugar que el mounstro debe usar como referencia hacia donde mirar cuando se mueve hacia su objetivo.

Escribiendolo en retrospectiva suena bastante simple, pero de lo que me enorgullezco es que no hay tutorial tan especifico para este problema que pudiera haber resuelto el problema. 

Aunque quizas entender que significa Vector3 o Transformhubiera ayudado.


{% highlight C# %}

{% endhighlight %}

[Igazi twitter][igazi-twitter]

[igazi-twitter]: https://twitter.com/igazikenyer
