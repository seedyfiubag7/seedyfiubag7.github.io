# Bitácora

La bitácora reúne entradas periódicas detallando el estado del proyecto en la fecha de su escritura. Se incluyen notas posteriores, que aclaran confusiones o diferencias de planes, que expliquen las diferencias más amplias con el producto final.



[TOC]



## 18 de Abril



### Frontend

Comienza el trabajo y con él la familiarización con las tecnologías del entorno de React Native, que hasta ahora son prácticamente desconocidas.  Gradualmente se desarrollan aplicaciones de mayor compeljidad:

<center><img src="b_img/1.jpg" alt="image10" width="800"/></center>



Las principales prioridades son definir un esquema general de la aplicación para organizar la navegación y determinar el modo en que se enseñarán los proyectos, que son el componente fundamental de toda la aplicación.

Se evaluaron bibliotecas de interfaz de usuario como UI Kitten, React Native UI Lib  y React Native Paper. Se optó por emplear esta última, pues su uso era sencillo y ofrecía un aspecto profesional y fluído.



### Backend

Al igual que en el frontend se comienza con la familiarizacion de las tecnologias, iniciando con una API Rest sencilla en javascript utilizando Express.

Adicionalmente los primeros modelos fueron evolucionando, incorporando una base de datos con PostgreSQL y comunicacion con Sequelize.

Por ultimo, se inicia el diseño de la arquitectura reconociendo rapidamente la necesidad de implementar un microservicio especializado en usuarios

## 13 de Mayo



### Frontend

<center><img src="b_img/2.jpg" alt="image10" width="600"/></center>



Inicialmente se dividieron las funciones de la aplicaciones en tres categorías: Proyectos, Mensajería y Perfiles (ver mockup izquierdo). En futuras iteraciones se determinó que, aunque la lectura inicial se simplificaría, la pantalla inicial contendría demasiada información y  que sería engorroso tener que seleccionar opciones del apartado de búsqueda para visualizar proyectos favoritos, patrocinados, etc  (ver mockup derecho).

<center><img src="b_img/4.png" alt="image10" width="400"/></center>

Para el registro y login no se plantea un diseño especialmente innovador, el esquema tradicional es eficaz.

Se trabaja en implementar dichas pantallas y especialmente en integrar el login con firebase.


### Backend

Con lo aprendido en los tutoriales seguidos se comienza por el ya mencionado microservicio de usuarios. Se decide utilizar como stack principal a javascript, node y postgresql. Ademas se decide que se utilizaran los servicios gratuitos de Heroku para el deployment de los microservicios

Se inicia la investigacion de autenticacion de clientes y se decide que esta sera delegada en el servicio de Firebase. En este punto se reconoce la necesidad de implementar un nuevo microservicio API Gateway que sirva de intermediario entre la comunicacion de los demas microservicios del backend y el frontend, facilitando de este modo cuestiones de autenticacion.

Se crean los repositorios de github independientes para API Gateway y Users Service

## 20 de Mayo



### Frontend



#### Pantalla Inicial

Cuando el usuario inicia la aplicación se encuentra con una pantalla en donde puede decidir si ingresar (con login corriente o federado) o registrarse. De ser posible, una vez que el usuario se ha registrado por primera vez, el ingreso se realizará automáticamente.

<center><img src="img/image10.png" alt="image10" width="350"/></center>



#### Pantalla de Registro

Se presentan múltiples campos que el usuario debe completar. Textos auxiliares en rojo informan errores.

En el futuro el botón de registro se deshabilitará hasta que no se detecten errores locales en los campos.

<center><img src="img/image14.png" alt="image20" width="350"/></center>



#### Pantalla de Ingreso

Análoga a la pantalla de registro.

<center><img src="img/image12.png" alt="image12" width="350"/></center>



#### Pantalla de Registro de Datos

Si el servidor no posee datos adicionales del usuario se lo conduce a la pantalla de registro de datos tras un ingreso/registro exitoso. El campo de fecha de nacimiento incluye formateo automático.

<center><img src="img/image16.png" alt="image16" width="350"/></center>



#### Pantalla Home

Cumple un doble propósito: Sirve de punto de entrada a la aplicación y presenta al usuario dos áreas de especial interés: sus proyectos y aquellos que considere favoritos.  Se listan tarjetas que reúnen un título y una imagen representativa.  Actualmente se debate si es conveniente trasladar las opciones que se presentan debajo al interior del proyecto y acceder al mismo solo con un click/toque sobre la tarjeta.

<center><img src="img/image5.png" alt="image5" width="350"/></center>



Para pasar de un área a otra basta con deslizar hacia los lados.



<center><img src="img/image0.png" alt="image0" width="350"/></center>

Debajo, una barra de aplicaciones permite navegar entre el resto de las pantallas principales,  mostradas a continuación.



#### Pantalla Búsqueda

El menú que permite buscar por diversos criterios se desplegará solo cuando el usuario selecciona la barra. 

Tras una búsqueda se presentará un listado muy similar al de Home.

<center><img src="img/image4.png" alt="image4" width="300"/></center>



*Retrospectiva: Inicialmente los usuarios se buscarían junto con los proyectos. Más tarde se decidió que tal enfoque no era intuitivo, ni sencillo de implementar. Además el objetivo del chat no es conectar con amigos o socios, sino con los dueños de los proyectos, por lo que tiene más sentido acceder a la conversación desde un proyecto.*



#### Pantalla de Mensajería

Esta pantalla reúne a aquellos usuarios con los que se haya comunicado mediante mensaje privado. El mecanismo de navegación entre salas y el propio intercambio de chats funciona a nivel de mockups. 

<center><img src="b_img/5.jpg" alt="image2" width="450"/></center>



El modo en que se interactúa por primera vez  con otro usuario aún no se ha determinado.



#### Pantalla de Cuenta

El contenido de esta pantalla es muy pobre de momento y quizás ni siquiera se permita establecer una imagen de perfil. Desde luego, se incorporarán campos y opciones de cuenta conforme evolucione la aplicación.

<center><img src="img/image1.png" alt="image1" width="350"/></center>


### Backend

Se termina de modelar el microservicio de usuarios, con su respectiva base de datos y una API Rest tipo crud. Ademas se agregan los primeros tests utilizando el framework de Jest y Supertest.

Se consigue la autenticacion con el sdk de Firebase en API Gateway y se la integra a un contenedor de Dockerfile, lo que permite posteriormente completar el camino de CI en el repositorio de Github y obtener el deployment a Heroku.

Por ultimo se estandarizan ciertas cuestiones de estructura de los microservicios y formato de codigo.

## 27 de Mayo



### Frontend



#### Veeduría

La sección de veeduría atraviesa varios de los procesos que involucra el trabajo. Se debatió entre añadir una nueva pestaña a la barra inferior o simplemente incluirlo en una sub-pestaña de proyectos. Tras un largo debate se optó por la segunda opción, pero cambiando las secciones a íconos, para simplificar el aspecto.

<center><img src="b_img/8.png" alt="image1" width="350"/></center>



#### Creación y visualización de proyectos

Habiendo establecido la estructura y tema general de la aplicación, es prioritario terminar de decidir el diseño de los proyectos, tanto a la hora de su creación, como al momento de su visualización.

<center><img src="b_img/7.png" alt="image1" width="350"/></center>

*Retrospectiva: Notar la ausencia de las etapas fijadas por el usuario. En un principio el equipo del front-end las había confundido por los estados del proyecto. Por ello el importe se establece en un único lugar.*

Respecto a la ubicación en la creación del proyecto, actualmente investigamos servicios de terceros que permitan indicarla de un modo más ameno, sin tener que conocer explícitamente la longitud y latitud del lugar que se requiere.

<center><img src="b_img/6.png" alt="image1" width="350"/></center>



El ícono de lápiz, que permite editar la descripción solo aparecerá cuando el dueño visualice su propio proyecto. Los comentarios públicos pueden no incluírse en la versión final, pero de desarrollarse definitivamente se ubicarán debajo de todos los demás componentes.


### Backend


Se dockeriza el servicio de usuarios, se realiza un refactor de este y se establece el deployment a Heroku a traves de Github utilizando CI.

Se mejora el modelado de la arquitectura, se reconoce la necesidad de al menos dos nuevos microservicios, el de proyectos y el de sponsors y veedores. 

Se decide comenzar por el modelado del servicio de proyectos utilizando como template el servicio de usuarios ya creado, lo que permitio obtener una API tipo crud en poco tiempo.


## 6 de Junio



### Frontend



#### Subida de imágenes

<center><img src="b_img/10.png" alt="image1" width="350"/></center>

Las pantallas anteriormente descritas funcionan, aunque con algunos errores. Hemos implementado una grilla de imágenes en la creación del proyecto, de forma tal que un usuario puede reordenar las imágenes que carga sin tener que borrarlas y resubirlas. Esto también soluciona el problema de cuál imagen mostrar en las búsquedas, pues si reordenar es sencillo, puede tomarse la primera de ellas como portada.



#### Ubicación

La biblioteca de Google Places Autocomplete provee un componente que se ajusta a nuestras necesidades, aunque presenta muchos problemas a la hora de renderizarse.

 
### Backend

El modelado del proyecto fue alterado ya que no cumplia con los requisitos, agregando asi un estado y lugar geografico. La implementacion de un posicionamiento geografico para cada proyecto fue ardua en un principio, ya que fue dificil de implementar tanto en PostgreSQL, como en sequelize y por ultimo Heroku. Se decidio utilizar el tipo de dato GEOMETRY, provisto por la biblioteca postgis de PostgreSQL.

Una vez se tuvo la primer version del servicio de proyectos, se integraron tests unitarios y se realizaron las primeras busquedas geograficas sencillas, sin implementar endpoints para estas.

Por ultimo se trabajaron los tests unitarios y documentacion en Swagger tanto en API Gateway como en proyectos.


## 13 de Junio



### Frontend



<center><img src="b_img/9.png" alt="image1" width="450"/></center>



Se trabaja en la integración de las búsquedas. La pantalla anterior recordaba demasiado a un formulario, donde la mayor parte de las opciones no se utilizaban.  Se modifico a un menú desplegable, donde la opción de búsqueda por defecto es por tags, y tocando en los 3 puntos el usuario puede acceder a los otros criterios , y si lo desea combinarlos.

<center><img src="b_img/11.png" alt="image1" width="250"/></center>

La administración del componente de paginación presentó grandes desafíos que pudieron para resolverse precisaron un replanteamiento total de la pantalla.


### Backend

Con una mejor comprension del modelo de negocio se decidio realizar un refactor al microservicio de proyectos, con el objetivo de incluir imagenes y tags a estos, lo que llevo bastante tiempo de investigacion debido a la necesidad de crear y vincular varias tablas en la base de datos.

Se agrego ademas la primera version del endpoint de busquedas de proyectos, permitiendo busquedas geograficas y por tags, con capacidad de paginacion.

Por otro lado, se avanzo sobre tests de integracion y permisos de usuarios en el microservicio de API Gateway

Por ultimo se comenzo el modelado del microservicio de sponsors y veedores, utilizando como template los microservicios anteriormente creados.


## 20 de Junio



### Frontend

<center><img src="b_img/12.png" alt="image1" width="600"/></center>

<center><img src="b_img/13.png" alt="image1" width="600"/></center>

Como parte de la refactorización de procesos, se replanteó la jerarquía de pantallas respecto a su navegación.

### Backend


Se mejora el microservicio de sponsors, agregando la posibilidad de sponsorear un proyecto e integrandolo a API Gateway.

Se finalizan los endpoints de busqueda en el microservicio de proyectos y se lo integra a API Gateway, actualizando la documentacion de esta ultima.

Ademas se crea el microservicio de payments, el cual brindara soporte a las wallets de los usuarios y una interfaz de comunicacion al smart contract

## 27 de Junio


### Frontend

<center><img src="b_img/14.png" alt="image1" width="350"/></center>

Para reflejar las nuevas características del back-end se actualizó el perfil, con un fondo agradable y nueva información de billeteras, veeduría y cierre de sesión.

### Backend

Se mejora el microservicio de sponsors, agregando soporte a creacion de veedores y revision de proyectos. Se añaden ademas tests unitarios sobre este microservicio.

Se conecta a API Gateway con el microservicio de sponsors y se agregan tests de integracion.

Se comienza a trabajar sobre el smart contract, lo que permite una comprension completa del modelo de negocio, que trae aparejados cambios en el modelado de proyectos, principalmente en la redefinicion de las categorias, estados y etapas de los proyectos.

## 8  de Julio



### Frontend

<center><img src="b_img/16.png" alt="image1" width="350"/></center>



Se solucionan errores y se refactoriza código.  Se pule la interfaz agregando pantallas de carga, mensajes de errores y mejor feedback ante el usuario.


### Backend


Se agrega soporte a voto de veedores en el microservicio de sponsors y se integra esta actualizacion a API Gateway, actualizando su documentacion.

Se crea el microservicio de notificaciones, tomando como tecnologias a python, FastAPI y SQLAlchemy y utilizando como servicio de push notifications a Firebase.

## 15 de Julio



### Frontend



Se terminó de implementar la funcionalidad del chat aprovechando la base de datos en tiempo real de Firebase. Se determinó que el contacto inicial se realice exclusivamente a través del perfil al que se accede dentro de la vista de proyecto. La sincronización de contactos conllevó sortear algunas dificultades menores, pero el resultado es robusto.



## 22 de Julio



### Frontend

<center><img src="b_img/15.png" alt="image1" width="350"/></center>

Implementar las notificaciones resultó mucho más complicado de lo esperado, pues el soporte de Firebase en Android e IOS es parcial. Tras múltiples intentos fallidos de evitar o circunventar éstas incompatibilidades afortunadamente se descubrió que el servicio de notificaciones de Expo es independiente de Firebase. 

### Backend

Se avanza sobre el microservicio de payments, se decide deployar el nodo del smart contract en un servidor de AWS ya que los servicios gratuitos de Heroku tienen mal rendimiento.

Se refactoriza el microservicio de notificaciones para brindar soporte a suscripciones a proyectos y se cambia el servicio de push notifications de Firebase por el de Expo

Se integra el microservicio de notificaciones a la API Gateway y se realizan los primeros testeos manuales.

## 29 de Julio



### Frontend



Se solucionan errores y se pule la interfaz agregando pantallas de carga, mensajes de errores y mejor feedback ante el usuario.


### Backend

Se mejora la documentacion de todos los microservicios, se completan tests unitarios y se solucionan errores relacionados a las busquedas de proyectos, paginacion, creacion de wallets y deployment en Heroku.