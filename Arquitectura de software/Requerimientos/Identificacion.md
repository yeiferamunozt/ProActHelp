Estos requisitos proporcionan una base sólida para el diseño e implementación del sistema, abordando las necesidades específicas identificadas en la reunión con el cliente, fueron identificados con el método de historias de usuario, los actores, requisitos funcionales y no funcionales se describen a continuación.

> En lo que corresponde a la definición de los requisitos el termino "gestionar" se refiere a las acciones de registrar, consultar, actualizar, eliminar y descargar.

# Actores

**Beneficiario:** Persona que requiere ayuda humanitaria, puede ser individuo o cabeza de familia, si pertenece a una familia los miebros de la familia tambien son beneficiarios y estaran vinculados entre si.

**Voluntario:** Persona que se ofrece para colaborar en la entrega de ayuda humanitaria, puede ser individuo o pertenecer a una organización.

**Organización cooperante:** Entidad que colabora en la entrega de ayuda humanitaria, puede ser una empresa, una fundación, una ONG, una entidad gubernamental.

**Organización de base:** Entidad que representa a un grupo de personas que requieren ayuda humanitaria, puede ser una asociación de vecinos, una asociación de comerciantes, una asociación de productores, una asociación de campesinos, puede convertirse en una organización cooperante.

**Administrador de territorio:** Persona encargada de gestionar la información del sistema, puede ser un líder comunitario o un líder de la fundación, requiere permisos para agregar, editar y eliminar información siempre y cuando no comprometa la integridad del sistema.

**Super Administrador:** Persona encargada de configurar el sistema en si, requiere conocimientos técnicos para realizar esta tarea, tiene acceso a todas las funcionalidades del sistema, incluyendo la gestión de usuarios y permisos.

**Semillero:** Grupo encargado del diseño, desarrollo y mantenimiento continuo del sistema tecnológico. Pueden incluir expertos en tecnologías de la información, personas con afinidad por la programación de la comunidad, estudiantes que deseen aportar a la comunidad.

**Usuario:** Todos los actores pueden ser usuarios del sistema, a los cuales se les asigna roles y permisos de acuerdo a sus responsabilidades dentro del proceso.

**Modelo analítico:** Proceso externo que se encarga de analizar la información del sistema y generar diagnósticos y predicciones sobre los beneficiarios.

# Requisitos Funcionales

## Gestión de Ayudas

Como Beneficiario, Organización base, Voluntario, Organización cooperante
Quiero consultar la información de registro de usuario
Para tener acceso a la información del registro de usuario y poder actualizarla en caso de ser necesario.

Como Beneficiario
Quiero consultar la información de núcleo familiar
Para tener acceso a la información del núcleo familiar y poder actualizarla en caso de ser necesario.

Como Beneficiario
Quiero consultar la información de la organización base
Para tener acceso a la información registrada de la organización base y de los miembros de la organización.

Como Beneficiario, Organización base
Quiero consultar información sobre las ayudas disponibles
Para conocer las ayudas disponibles en el territorio y solicitarlas en caso de necesitarlas.

Como Voluntario, Organización cooperante
Quiero consultar información sobre aportes
Para conocer los aportes realizados y su estado actual.

Como Voluntario, Organización cooperante
Quiero descargar un certificado de aportes
Para tener un registro de los aportes realizados y poder utilizarlo como soporte para cualquier trámite.

Como Administrador de territorio
Quiero gestionar la información de los territorios
Para tener un registro actualizado de su accesibilidad, beneficiarios y aliados locales, así como las necesidades específicas de cada territorio.

Como Administrador de territorio
Quiero gestionar la información de los beneficiarios
Para tener un registro completo y actualizado de las personas o familias que requieren ayuda humanitaria en cada territorio.

Como Administrador de territorio
Quiero gestionar la información de las organizaciones
Para tener un registro completo y actualizado de las entidades que pueden colaborar en la entrega de ayuda humanitaria.

Como Administrador de territorio
Quiero gestionar la información de los voluntarios
Para tener un registro completo y actualizado tanto a nivel individual como grupal, con el fin de contar con recursos humanos disponibles para apoyar en los procesos logísticos.

Como Administrador de territorio
Quiero gestionar los diferentes aportes
Para llevar un control adecuado de los aportes de cada individuo u organización de acuerdo a su tipo (dinero, en especie o trabajo).

## Medición de Impacto

Como Administrador de territorio
Quiero gestionar los indicadores de impacto
Para tener un registro completo y actualizado de los indicadores que se utilizarán para medir el impacto de las ayudas humanitarias.

Como Administrador de territorio, Organización cooperante, Voluntario, Organización base
Quiero registrar informacion a los indicadores utilizando formularios
Para facilitar la recopilación y registro de información relacionada con los indicadores, tanto en el método ex-ante como en él ex-post y metas de acuerdo al tipo de indicador (cuantitativo y cualitativo)

Como Modelo analítico
Quiero consultar información sobre los indicadores
Para tener acceso a la información de los indicadores y poder realizar análisis de datos.

Como Administrador de territorio, Organización cooperante, Modelo analítico
Quiero gestionar diagnósticos y predicciones
Para tener un control sobre los diagnósticos generados por el modelo analítico y poder realizar un seguimiento a las predicciones.

Como Administrador de territorio, Organización cooperante, Modelo analítico
Quiero gestionar prescripciones y recomendaciones
Para tener un control sobre las prescripciones ajustadas a cada diagnóstico y poder realizar un seguimiento a las recomendaciones.

Como Administrador de territorio, Organización cooperante, Organización base
Quiero consultar historias de beneficiarios
Para contar con un registro detallado sobre cada beneficiario, que incluya información personal, así como contexto ambiental, emocional, social y económico. 

## Interoperabilidad

Como Administrador de territorio, Organización cooperante, Organización base
Quiero gestionar proyectos
Para planificar y coordinar las actividades necesarias para la entrega de ayuda humanitaria, incluyendo la asignación de responsables y el seguimiento de los tiempos de ejecución.

Como Administrador de territorio, Organización cooperante, Organización base
Quiero gestionar tareas dentro de cada proyecto
Para desglosar las actividades en acciones más pequeñas y medir su progreso individualmente.

Como Administrador de territorio, Organización cooperante, Organización base
Quiereo visualizar proyectos y tareas con diferentes vistas
Para tener una visión general de los proyectos y tareas, así como de su estado actual es necesario contar con diferentes vistas (gannt, tablero kanban, lista, calendario) que permitan filtrar y ordenar la información de acuerdo a las necesidades de cada usuario.

Como Administrador de territorio, Organización cooperante, Organización base
Quiero asignar responsables a cada tarea
Para asegurar que haya una persona responsable designada para llevar a cabo cada actividad dentro del proyecto.

Como Administrador de territorio, Organización cooperante, Organización base
Quiero medir los tiempos de ejecución de las tareas realizadas
Para tener un registro preciso del tiempo que toma completar cada actividad y así identificar posibles retrasos o ineficiencias en el proceso logístico, además de poder realizar una mejor estimación y valoración de los recursos necesarios para la ejecución de cada proyecto.

Como Voluntario, Beneficiario, Organización cooperante, Organización base
Quiero consultar información sobre los proyectos
Para conocer el estado actual de los proyectos logísticos humanitarios y poder colaborar en su ejecución.

Como Voluntario, Organización cooperante, Organización base
Quiero gestionar tareas o apoyar en su ejecución
Para tener un registro de las tareas que he realizado y su estado actual.

## Gestion del sistema

Como Administrador de territorio
Quiero gestionar usuario para organizaciones, entidades e individuos
Para fomentar la colaboración entre distintas entidades involucradas en la entrega de ayuda humanitaria, facilitando el intercambio fluido de datos e información relevante operando con la misma base de información.

Como Administrador de territorio
Quiero gestionar diferentes roles y permisos
Para garantizar que solo las personas autorizadas puedan acceder al sistema y realizar acciones específicas según sus responsabilidades dentro del proceso logístico.

Como Administrador de territorio, Semillero
Quiero gestionar tutoriales integrados en el sistema
Para facilitar la comunicación sobre el uso del sistema y las funcionalidades disponibles a los usuarios.

Como Usuario
Quiero consultar tutoriales
Para aprender rápidamente cómo utilizar eficientemente todas las funcionalidades disponibles sin necesidad de formación adicional.

Como Usuario
Quiero iniciar sesión en el sistema
Para tener acceso a las funcionalidades disponibles de acuerdo a mis permisos.

Como Usuario
Quiero cerrar sesión en el sistema
Para garantizar la seguridad de mi información y evitar accesos no autorizados.

Como Usuario
Quiero recuperar contraseña
Para poder acceder al sistema en caso de olvidar mi contraseña.

Como Usuario
Quiero cambiar contraseña
Para controlar la seguridad de mi usuario y evitar accesos no autorizados.

Como Semillero
Quiero consultar información mediante una API
Para poder acceder a la información del sistema desde la interfaz o integrarlo con otras herramientas.

### No Funcionales

Quiero usar el sistema en Android, iPhone, Windows, Mac y Linux
Para poder acceder a la plataforma desde cualquier dispositivo o sistema operativo que utilice.

Quiero usar el sistema sin depender de licencias de pago externas
Para minimizar los costos asociados al uso y mantenimiento del sistema.

Quiero actualizar el sistema de modo uniforme en todos los dispositivos
Para asegurarme de tener siempre la última versión disponible sin importar desde qué dispositivo acceda al sistema.

Necesito ejecutar el sistema sin costo o de bajos costos de infraestructura
Para garantizar la sostenibilidad financiera a largo plazo.