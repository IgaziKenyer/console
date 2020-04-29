---
layout: post
title:  "Floor Manager"
date:   2020-04-29 16:55:35 -0400
categories: [gamedev, danmakui]
---
Floor Manager
Si estas en el primer piso, las balas deben chocar contra las paredes que se elevan al segundo piso.
Si estas en el segundo piso, las balas no deben chocar contra las paredes que se elevan al segundo piso.
Me revolvia la cabeza respecto a donde deberia colocar la logica de esto.
En las balas ? cuando estas choquen con las murallas?
En el Jugador ? cuando este suba al segundo Piso?
En las murallas ? cuando estas reciban las balas o el jugador este en cierta posicion?
Cada una de estas configuraciones requeriria manejarse con otro script en otro objecto.
Pero el que menos requeria esto era la configuracion de las murallas.

Cuando una bala colisiona con collider pregunta si es que este collider tiene el [Tag] Enemigo o Muralla si no lo tiene lo ignora, si los tiene 
-Le quita HP al enemigo con el que choco.
-Es destruida en caso de que sea una muralla
Eso funciona perfectamente.

Cada plataforma de segundo piso tiene a todas sus murallas en el mismo objeto y forman por ejemplo "Coleccion 1A" dentro de esta coleccion 1A existe un collider Poligonal 2D que funciona como trigger, o sea solo detecta si algo entro en su rango y junto con estos colliders cree un scrip [FloorControl]

Floor control usa esa informacion para reaccionar en caso de que el player salga o entre a la zona.

De ahi fue una cosa de sintaxis.

Conclusion
Cuando el player esta en el primer piso, las murallas que se elevan al segundo piso tienen el [Tag] [Muralla] por lo tanto las balas chocan y explotan.
Cuando el player esta en el segundo piso, [FloorControl] detecta eso y le quita el [Tag] [Muralla] Esto no les quita su propiedad de murallas con otras cosas que no sean balas asi que las balas pasan y el jugador no baja del segundo piso almenos que sea por la escalera.

