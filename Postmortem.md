# Post Mortem




## Introducción


En este documento se analizan las posibles causas de demoras, las estrategias adoptadas para resolver los más grandes desafíos en los que se incurrió  y las lecciones aprendidas de cara a futuros proyectos.

A grandes rasgos la principal causa de demoras y fracasos resultó de la inexperiencia en el entorno de las tecnologías utilizadas. Al no contar con instancias previas que sirvan de referencia se juzgó la dificultad y prioridad de las tareas pobremente, siendo el caso más grosero las Notificaciones.  Otra consecuencia de la ignorancia en los temas tratados fue una reducción en el grado de independencia del front-end y el back-end, generando que en ocasiones no pueda implementarse una interfaz por desconocer la estructura de la información con la que se contará o existan procesos en el back-end que temporalmente no sean aprovechados en el front-end.



## API REST

REST es excelente para organizar el trabajo, pues fácilmente pueden esbozarse los puntos de interacción y trabajar simultáneamente en el front-end y el back-end. No obstante, para ello debe haberse desarrollado una intuición del modo en que se representará finalmente la información, que no adquirimos hasta mitad del cuatrimestre. De cara al futuro no dudaremos en operar de este modo, que resultó muy eficaz.




## Volatilidad de tecnologías


A diferencia de otros ambientes más tradicionales en los que se ha instalado un núcleo duro de bibliotecas que resuelven las problemáticas más frecuentes, las librerías exploradas ofrecían un conjunto de métodos y formas de uso muy inestables. Se encontraron muchas bibliotecas descontinuadas o con documentación desactualizada, si es que presentaban alguna.

Aunque hacia el futuro ya se contará con nociones del uso de las bibliotecas elegidas, más provechoso resultaría destinar las etapas tempranas del proyecto a construir ejemplos mínimos, representativos de las partes  más inciertas del trabajo, a modo de afinar el juicio de complejidad y los plazos esperados.
















## Dependencia de periodos de prueba


La noche anterior al checkpoint final del TP las pruebas comenzaron a fallar y los servicios se interrumpieron súbitamente. Se había alcanzado la cuota mensual del plan gratuito por aplicación de Heroku, servidor utilizado para hostear los microservicios del backend.


Sumado a ello, la constante intermitencia en la disponibilidad de los microservicios dificultó en gran medida la detección de errores, pues un leve descuido podría generar inconsistencias en la base de datos, que repercutían en todo el sistema e indirectamente en el front-end.

No existe una lección muy profunda que aprender, de hecho somos afortunados de que empresas brinden servidores de prueba gratuitos en primer lugar, simplemente es un aspecto al que debe prestársele mucha atención a medida que crece el sistema que se desarrolla.




## El Smart-Contract y su rol dentro del Trabajo Práctico


El manejo del smart-contract es interesante y una vez desplegado brinda una buena solución al flujo de fondos. No obstante fue muy difícil de depurar en las redes de testing y como la mayor parte de los servicios dependían de él, implicó una parálisis temporal en el avance del proyecto. Si bien se trató de dockerizar el nodo de manera que quede integrado a la red de microservicios, esto presentaba problemas de memoria y no se lograban minar todas las transacciones.

Hacia el futuro, el correcto funcionamiento del smart contract será prioritario y se probará tempranamente a nivel local, con una test-net propia (como la  provista por Hardhat) para la asegurar correcta evolución del proyecto.



## Deudas Técnicas




### Tests 


A pesar de que se consiguió superar los requisitos de cobertura en tests unitarios y de integración, (a excepción del servicio de notificaciones), se cree que en caso de contar con mayor tiempo disponible los tests podrían haber sido más abundantes y más específicos, siendo que en algunos de ellos se probaron únicamente los casos felices de ejecución.
Del mismo modo, haber contado con acceso desde el propio repositorio de Github al detalle completo del análisis de cobertura de los tests en cada servicio podría haber resultado más cómodo que observar los detalles de la ejecución del script de CI.


### Métricas


El TP final cuenta con recopilación de métricas sencillas que son calculadas a tiempo real cuando éstas son requeridas. En retrospectiva, una mejor implementación habría sido crear un microservicio especializado en recopilación periódica de métricas o bien adaptar algún agente de recopilación , como los provistos por DataDog.


### Logs


En el TP se cuenta con logs configurables en cada microservicio, a través de variables de entorno, sin embargo los dynos de Heroku sobre los cuales fueron hosteados permiten ver únicamente los logs más recientes, perdiendo así información útil de corridas pasadas. Habría sido interesante sincronizar un servicio de persistencia de logs, como provee DataDog


### Documentación


Fue vital para la correcta comunicación entre back-end y front-end tener una documentación de la API Gateway completa y actualizada. Este no fue el caso en ciertos servicios internos, pues su documentación no era prioritaria. En consecuencia, en algunos casos pueden encontrarse desactualizadas o incompletas. Aunque para el alcance de éste trabajo práctico esto no supone un problema, reconocemos que en proyectos de mayor envergadura debería dedicarse un esfuerzo mayor a mantener reportes internos consistentes con la implementación.


### Inconsistencia de datos


Un punto sumamente importante al momento del desarrollo de un backend, y aún más en uno basado en microservicios, es evitar o cubrir las ocasionales inconsistencias de datos que pueden darse. En general debido a baja de los servidores. Así se evaden frustraciones al momento de manejar la aplicación, como lo es no disponer de una billetera válida al crear la cuenta.
Algunos de dichos errores aún pueden ocurrir, ya que las técnicas de atomización de requests (como ser las transacciones)  requieren una capacidad de diseño cuidadoso, de la que se carecía en la primer mitad del cuatrimestre y que no pudo compensarse más adelante, en pos de lograr la integración completa  con el cliente en tiempo y forma.