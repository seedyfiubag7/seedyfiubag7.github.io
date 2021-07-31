# Manual de Usuario Backoffice

## Índice

{% capture markdown %}

## Introducción

El Backoffice es una aplicación web diseñada para la supervisión y control de usuarios y proyectos. Se puede utilizar ingresando en: https://seedyfiuba-autenticacion.web.app/

## Primeros Pasos

### Creación de Cuenta

Si es la primera vez que utiliza el servicio de Backoffice o busca crearse una nueva cuenta, debe seguir los siguientes pasos:

* En la página inicial, seleccione 'Registrarse'.

<center><img src="img/**PNG" width="950"/></center>

* Complete las credenciales con un mail válido, y una contraseña de al menos 6 caracteres. Una vez completado, presione 'REGISTRARSE'.

<center><img src="img/*PNG" width="950"/></center>

* Complete el apartado de nombre y apellido, y seleccione su fecha de nacimiento haciendo click en el calendario a la derecha del campo. Al finalizar, presione 'REGISTRARSE'.

<center><img src="img/*PNG" width="950"/></center>

* Una vez finalizado el registro, se lo llevará a la pantalla principal del Backoffice, donde le aparecerá un mensaje de error hasta que se le otorgue el poder de administrador. Dicho poder debe ser solicitado a un administrador del sistema.

### Ingreso con Cuenta Propia

* En la página principal, ingrese las credenciales de la cuenta anteriormente creada y seleccione 'INGRESAR'.

<center><img src="img/*PNG" width="950"/></center>

### Recupero de Contraseña

* En la página inicial, seleccione 'Recuperar contraseña'.

<center><img src="img/**PNG" width="950"/></center>

* Ingrese el mail asociado a su cuenta y presione 'ENVIAR MAIL'. Le aparecerá un mensaje cuando se envíe el mail. A continuación, vaya a la casilla de correos de su mail y siga las instrucciones.

<center><img src="img/*PNG" width="950"/></center>

## Administración de Usuarios

En la sección de Usuarios se podrán listar todos los usuarios del sistema, revisar la información detallada de cada uno y promocionar a administrador.

### Listado de Usuarios

* Al ingresar a la sección de Usuarios, se listarán una cantidad predeterminada de usuarios.

<center><img src="img/*PNG" width="950"/></center>

* Para ver más usuarios, vaya hacia abajo en la página y presione el botón para avanzar o para retroceder (éstas aparecerán en gris y deshabilitadas en caso de que no haya más usuarios que mostrar).

<center><img src="img/**PNG" width="950"/></center>

### Información de un Usuario y Promoción a Administrador

* Para acceder a la información de un usuario, haga click en los '...' del usuario que busca.

<center><img src="img/**PNG" width="950"/></center>

* Se lo redirigirá a una pantalla donde podrá ver toda la información del usuario seleccionado

<center><img src="img/*PNG" width="950"/></center>

* En caso de querer promocionar un usuario a administrador, se debe presionar sobre 'HACER ADMIN'.

<center><img src="img/**PNG" width="950"/></center>

## Administración de Proyectos

En la sección de Proyectos se podrán listar todos los proyectos del sistema, filtrar por distintos campos y revisar la información detallada de cada uno.

### Listado de Proyectos

* Al entrar a la sección de proyectos, se listarán todos los proyectos sin filtros. Para hacer una búsqueda con filtrado, completa los distintos campos y presione el botón para buscar.

   Los distintos campos son:

   - ID Usuario. Un ID único correspondiente a un usuario.
   - Etiquetas. Las etiquetas por las que se quiere buscar. Son case sensitive y se pueden escribir múltiples etiquetas separando por espacios.
   - Categoría. Categoría del proyecto, se puede seleccionar únicamente una o ninguna.
   - Etapa. Etapa del proyecto, se puede seleccionar únicamente una o ninguna.

<center><img src="img/*PNG" width="950"/></center>

* Para ver más proyectos, vaya hacia abajo en la página y presione el botón para avanzar o para retroceder (éstas aparecerán en gris y deshabilitadas en caso de que no haya más usuarios que mostrar).

<center><img src="img/1*PNG" width="950"/></center>

### Información de un Proyecto

* Para ingresar a un proyecto, presione sobre la tarjeta correspondiente. Será redirigido y podrá ver la información detallada del proyecto.

<center><img src="img/1*PNG" width="950"/></center>

## Métricas de Usuarios y Proyectos

En esta sección se encontrará con la información de las siguientes métricas:

* Cantidad de nuevos usuarios a lo largo del tiempo
* Cantidad de nuevos proyectos a lo largo del tiempo
* Cantidad de proyectos por etapa
* Cantidad de proyectos por categoría
* Cantidad de usuarios total vs usuarios veedores vs usuarios admins.

<center><img src="img/*PNG" width="950"/></center>

<center><img src="img/*PNG" width="950"/></center>

{% include toc.html html=text ordered=true %}
{{ text }}




