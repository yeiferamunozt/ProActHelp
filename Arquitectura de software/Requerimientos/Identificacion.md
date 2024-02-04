Estos requisitos proporcionan una base sólida para el diseño e implementación del sistema, abordando las necesidades específicas identificadas en la reunión con el cliente, fueron identificados con el método de historias de usuario, los actores, requisitos funcionales y no funcionales se describen a continuación.

> [!NOTE]
> En lo que corresponde a la definición de los requisitos el termino "gestionar" se refiere a las acciones de registrar, consultar, actualizar, eliminar y descargar.

# Actores

#### ACT-001
**Beneficiario:** Persona que requiere ayuda humanitaria, puede ser individuo o pertenecer a un grupo familiar, si pertenece a un grupo familiar los miebros de la familia tambien son beneficiarios y estaran vinculados entre si.

#### ACT-002
**Voluntario:** Persona que se ofrece para colaborar en la entrega de ayuda humanitaria, puede ser individuo, ser beneficiario, pertenecer al territorio, pertenecer a una organización cooperante o a una organización de base.

#### ACT-003
**Cooperante:** Persona natural, entidad o alianza interinstitucional que patrocina la acción humanitaria, puede ser un individuo, una empresa mercantil, una entidad sin animo de lucro, una entidad gubernamental o una entidad académica, cada entidad puede ser internacional o nacional, o la alianza de varias entidades.

#### ACT-004
**Organización de base:** Entidad formal o colectivo comunitario que representa a un grupo de personas que requieren ayuda humanitaria, puede ser una organización sin animo de lucro con un bajo nivel de formalización o una iniciativa colectiva de diferentes individuos no formalizada, pueden convertirsen en una organización cooperante.

#### ACT-005
**Administrador de territorio:** Persona encargada de gestionar la información del sistema, puede ser un individuo delegado por la organización de base o la organización cooperante, requiere permisos para agregar, editar y eliminar información siempre y cuando no comprometa la integridad del sistema, dentro del lenguaje scrum se le conoce como product owner.

#### ACT-006
**Super Administrador:** Persona encargada de configurar el sistema en si, requiere conocimientos técnicos para realizar esta tarea, tiene acceso a todas las funcionalidades del sistema, incluyendo la gestión de usuarios y permisos.

#### ACT-007
**Semillero:** Grupo encargado del diseño, desarrollo y mantenimiento continuo del sistema tecnológico. Pueden incluir expertos en tecnologías de la información, personas con afinidad por la programación de la comunidad o estudiantes que deseen aportar a la comunidad.

#### ACT-008
**Usuario:** Todos los actores pueden ser usuarios del sistema, a los cuales se les asigna roles y permisos de acuerdo a sus responsabilidades dentro del proceso.

#### ACT-009
**Modelo analítico:** Entidad externa que se encarga de analizar la información del sistema y generar informacion estrategica acerca de la oferta y demanda de acciones humanitarias.

# Requisitos Funcionales

## (MOD-001) Gestión de Ayudas

#### RQF-001
Como Usuario
Quiero **gestionar la información de registro de usuario de acuerdo a permisos**
Para tener acceso a la información del registro de usuario y poder actualizarla en caso de ser necesario.

#### RQF-002
Como Beneficiario
Quiero **gestionar la información del grupo familiar**
Para tener acceso a la información del grupo familiar y poder actualizarla en caso de ser necesario.

#### RQF-003
Como Beneficiario
Quiero **consultar la información de la organización base**
Para tener acceso a la información registrada de la organización base y de los miembros de la organización.

#### RQF-004
Como Beneficiario, Organización base
Quiero **consultar información sobre las ayudas disponibles y asignadas**
Para conocer las ayudas disponibles en el territorio y solicitarlas en caso de necesitarlas.

#### RQF-005
Como Voluntario, Organización cooperante
Quiero **consultar información sobre aportes propios**
Para conocer los aportes realizados y su estado actual.

#### RQF-006
Como Voluntario, Organización cooperante
Quiero **descargar certificado de aportes propios**
Para tener un registro de los aportes realizados y poder utilizarlo como soporte para cualquier trámite.

#### RQF-007
Como Administrador de territorio
Quiero **gestionar la información de los territorios**
Para tener un registro actualizado de su accesibilidad, beneficiarios y aliados locales, así como las necesidades específicas de cada territorio.

#### RQF-008
Como Administrador de territorio
Quiero **gestionar la información de los beneficiarios**
Para tener un registro completo y actualizado de las personas o familias que requieren ayuda humanitaria en cada territorio.

#### RQF-009
Como Administrador de territorio
Quiero **gestionar la información de las organizaciones**
Para tener un registro completo y actualizado de las entidades que pueden colaborar en la entrega de ayuda humanitaria.

#### RQF-010
Como Administrador de territorio
Quiero **gestionar la información de los voluntarios**
Para tener un registro completo y actualizado tanto a nivel individual como grupal, con el fin de contar con recursos humanos disponibles para apoyar en los procesos logísticos.

#### RQF-011
Como Administrador de territorio
Quiero **gestionar los diferentes aportes de acuerdo a permisos**
Para llevar un control adecuado de los aportes de cada individuo u organización de acuerdo a su tipo (dinero, en especie o trabajo).

## (MOD-002) Medición de Impacto

#### RQF-012
Como Administrador de territorio
Quiero **gestionar los indicadores de impacto**
Para tener un registro completo y actualizado de los indicadores que se utilizarán para medir el impacto de las ayudas humanitarias.

#### RQF-013
Como Administrador de territorio, Voluntario
Quiero **registrar informacion a los indicadores utilizando formularios**
Para facilitar la recopilación y registro de información relacionada con los indicadores, tanto en el método ex-ante como en él ex-post y metas de acuerdo al tipo de indicador (cuantitativo y cualitativo)

#### RQF-014
Como Modelo analítico
Quiero **consultar información sobre los indicadores y resultados de modelos de acuerdo a permisos**
Para tener acceso a la información de los indicadores y poder realizar análisis de datos.

#### RQF-015
Como Administrador de territorio, Organización cooperante, Modelo analítico
Quiero **gestionar diagnósticos y predicciones de acuerdo a permisos**
Para tener un control sobre los diagnósticos generados por el modelo analítico y poder realizar un seguimiento a las predicciones.

#### RQF-016
Como Administrador de territorio, Organización cooperante, Modelo analítico
Quiero **gestionar prescripciones y recomendaciones de acuerdo a permisos**
Para tener un control sobre las prescripciones ajustadas a cada diagnóstico y poder realizar un seguimiento a las recomendaciones.

#### RQF-017
Como Administrador de territorio, Organización cooperante
Quiero **consultar historias de vida de acuerdo a permisos**
Para contar con un registro detallado sobre cada beneficiario, que incluya información personal, así como contexto ambiental, emocional, social y económico. 

## (MOD-003) Interoperabilidad

#### RQF-018
Como Administrador de territorio
Quiero **gestionar proyectos**
Para planificar y coordinar las actividades necesarias para la entrega de ayuda humanitaria, incluyendo la asignación de responsables y el seguimiento de los tiempos de ejecución.

#### RQF-019
Como Organización cooperante
Quiero **gestionar procesos especificos dentro de cada proyecto**
Para desglosar las actividades en acciones más pequeñas y medir su progreso individualmente.

#### RQF-020
Como Organización cooperante, Organización base
Quiereo **visualizar proyectos y tareas con diferentes vistas**
Para tener una visión general de los proyectos y tareas, así como de su estado actual es necesario contar con diferentes vistas (gannt, tablero kanban, lista, calendario) que permitan filtrar y ordenar la información de acuerdo a las necesidades de cada usuario.

#### RQF-021
Como Administrador de territorio, Organización cooperante
Quiero **asignar responsables a cada proceso**
Para asegurar que haya una persona responsable designada para llevar a cabo cada actividad dentro del proyecto.

#### RQF-022
Como Voluntario
Quiero **medir y categorizar los tiempos de ejecución de las tareas realizadas**
Para tener un registro preciso del tiempo que toma completar cada actividad y así identificar posibles retrasos o ineficiencias en el proceso logístico, además de poder realizar una mejor estimación y valoración de los recursos necesarios para la ejecución de cada proyecto.

#### RQF-023
Como Voluntario, Beneficiario, Organización cooperante, Organización base
Quiero **consultar información sobre los proyectos**
Para conocer el estado actual de los proyectos logísticos humanitarios y poder colaborar en su ejecución.

#### RQF-024
Como Administrador de territorio, Voluntario, Organización cooperante, Organización base
Quiero **gestionar subprocesos y tareas o apoyar en su ejecución**
Para tener un registro de las tareas que he realizado y su estado actual.

## (MOD-004) Gestion del sistema

#### RQF-025
Como Administrador de territorio
Quiero **gestionar usuario para los actores del sistema**
Para fomentar la colaboración entre distintas entidades involucradas en la entrega de ayuda humanitaria, facilitando el intercambio fluido de datos e información relevante operando con la misma base de información.

#### RQF-026
Como Administrador de territorio
Quiero **gestionar diferentes roles y permisos**
Para garantizar que solo las personas autorizadas puedan acceder al sistema y realizar acciones específicas según sus responsabilidades dentro del proceso logístico.

#### RQF-027
Como Administrador de territorio, Semillero
Quiero **gestionar tutoriales integrados en el sistema**
Para facilitar la comunicación sobre el uso del sistema y las funcionalidades disponibles a los usuarios.

#### RQF-028
Como Usuario
Quiero **consultar tutoriales**
Para aprender rápidamente cómo utilizar eficientemente todas las funcionalidades disponibles sin necesidad de formación adicional.

#### RQF-029
Como Usuario
Quiero **iniciar sesión en el sistema**
Para tener acceso a las funcionalidades disponibles de acuerdo a mis permisos.

#### RQF-030
Como Usuario
Quiero **cerrar sesión en el sistema**
Para garantizar la seguridad de mi información y evitar accesos no autorizados.

#### RQF-031
Como Usuario
Quiero **recuperar contraseña**
Para poder acceder al sistema en caso de olvidar mi contraseña.

#### RQF-032
Como Usuario
Quiero **cambiar contraseña**
Para controlar la seguridad de mi usuario y evitar accesos no autorizados.

#### RQF-033
Como Semillero
Quiero **consultar información mediante una API**
Para poder acceder a la información del sistema desde la interfaz o integrarlo con otras herramientas.

### No Funcionales

#### RQNF-001
Quiero **usar el sistema en Android, iPhone, Windows, Mac y Linux**
Para poder acceder a la plataforma desde cualquier dispositivo o sistema operativo que utilice.

#### RQNF-002
Quiero **usar el sistema sin depender de licencias de pago externas**
Para minimizar los costos asociados al uso y mantenimiento del sistema.

#### RQNF-003
Quiero **actualizar el sistema de modo uniforme en todos los dispositivos**
Para asegurarme de tener siempre la última versión disponible sin importar desde qué dispositivo acceda al sistema.

#### RQNF-004
Necesito **ejecutar el sistema sin costo o de bajos costos de infraestructura**
Para garantizar la sostenibilidad financiera a largo plazo.