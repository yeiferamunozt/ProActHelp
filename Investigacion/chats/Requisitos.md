---
system_commands:
  - Deberás actuar como un experto arquitecto de software certificado como scrum máster
temperature: 0
top_p: 1
max_tokens: 3201
presence_penalty: 1
frequency_penalty: 1
stream: true
stop: 
n: 1
model: gpt-4
---
Tu tarea consiste en convertir a historias de usuario los siguientes requerimientos para un proyecto de software, se te proporcionará la descripción general del problema que el software pretende abordar y los requerimientos identificados. Beberás crear historias de usuario tomando como contexto la situación actual y la situación potencial para este proyecto, en la lista de requerimientos que se te proporcionará encontrarás notas adicionales indicadas con el símbolo ">" y los requerimientos con el símbolo "-". Para generar las historias de usuario, tener en cuenta que las entrevistas se hicieron con el líder de una fundación en la comunidad, generaras una historia de usuario por cada requisito listado.

Situación actual: 

La logística humanitaria en la localidad de Usme, Bogotá, Colombia se encuentra desorganizada y es ineficiente. Existen procesos manuales y repetitivos que son propensos a errores que afectan la calidad de la ayuda entregada o directamente no se lleva control ni historial sobre los procesos. Además, existe una falta de planificación y organización en el manejo de los recursos. 

Situación potencial:  

Se busca diseñar un sistema tecnológico que permita optimizar los procesos logísticos humanitarios. Este sistema deberá ser capaz de coordinar múltiples actores y recursos para mejorar la eficiencia y efectividad en la entrega de ayuda humanitaria. Adicionalmente, se espera que este proyecto promueva el desarrollo sostenible al cumplir con las metas del ODS 12: Producción y consumo responsables.

## Gestión de Ayudas

> Cada territorio tendrá información sobre accesibilidad, beneficiarios y aliados locales, conjunto de necesidades y la relación entre ellos.

- Gestionar información de territorios.
- Gestionar beneficiarios en cada territorio.
- Gestionar organizaciones en cada territorio.

<hr class="__chatgpt_plugin">

role::assistant
## Gestión de Ayudas

Como administrador del sistema
Quiero poder gestionar la información de los territorios
Para tener un registro actualizado de su accesibilidad, beneficiarios y aliados locales, así como las necesidades específicas de cada territorio.

Como administrador del sistema
Quiero poder gestionar la información de los beneficiarios
Para tener un registro completo y actualizado de las personas o familias que requieren ayuda humanitaria en cada territorio.

Como administrador del sistema
Quiero poder gestionar la información de las organizaciones
Para tener un registro completo y actualizado de las entidades que pueden colaborar en la entrega de ayuda humanitaria.

<hr class="__chatgpt_plugin">

role::user
## Interoperabilidad

> El sistema permitirá la planificación y gestión de proyectos logísticos humanitarios.
> Deberá medir los tiempos de ejecución de tareas y asignar responsables
> La herramienta debe cubrir aspectos estratégicos (Plan de trabajo), tácticos (Metodologías Scrum) y operativos (Gestion de tiempo).

- Gestionar proyectos.
- Gestionar tareas.
- Asignar responsables de tareas.
- Medir tiempos de ejecución de tareas.

> Diferentes organizaciones y entidades deben poder consultar, agregar y operar.
> Permitir que diferentes organizaciones y entidades trabajen con la misma base de información.
> Acceso a la información en cualquier momento.
> Se gestionarán permisos de acceso y restricciones según roles de usuarios.

- Gestionar usuarios.
- Gestionar permisos de acceso.
- Gestionar roles de usuarios.

> El sistema deberá poseer tutoriales integrados para que los usuarios puedan utilizarlo eficientemente con mínima formación.

- Gestionar tutoriales.
- Ver tutoriales.


<hr class="__chatgpt_plugin">

role::assistant

## Interoperabilidad

Como administrador del sistema
Quiero poder gestionar proyectos logísticos humanitarios
Para planificar y coordinar las actividades necesarias para la entrega de ayuda humanitaria, incluyendo la asignación de responsables y el seguimiento de los tiempos de ejecución.

Como administrador del sistema
Quiero poder gestionar tareas dentro de cada proyecto
Para desglosar las actividades en acciones más pequeñas y medir su progreso individualmente.

Como administrador del sistema
Quiero poder asignar responsables a cada tarea
Para asegurar que haya una persona responsable designada para llevar a cabo cada actividad dentro del proyecto.

Como administrador del sistema
Quiero poder medir los tiempos de ejecución de las tareas realizadas
Para tener un registro preciso del tiempo que toma completar cada actividad y así identificar posibles retrasos o ineficiencias en el proceso logístico.

Como administrador del sistema 
Quiero permitir que diferentes organizaciones y entidades consulten, agreguen y operen con la misma base de información.
Para fomentar la colaboración entre distintas entidades involucradas en la entrega de ayuda humanitaria, facilitando el intercambio fluido de datos e información relevante.

Como administrador del sistema 
Quiero gestionar usuarios con diferentes roles y permisos.
Para garantizar que solo las personas autorizadas puedan acceder al sistema y realizar acciones específicas según sus responsabilidades dentro del proceso logístico.

Como usuario registrado 
Quiero tener acceso a tutoriales integrados en el sistema.
Para aprender rápidamente cómo utilizar eficientemente todas las funcionalidades disponibles sin necesidad de formación adicional.

<hr class="__chatgpt_plugin">

role::user

### No Funcionales

- El sistema debe ser compatible con Android, iPhone, Windows, Mac y Linux.
- El sistemas no debe depender forzadamente de software con licenciamiento de pago.
- Las actualizaciones deben ser desplegadas de manera uniforme a todos los usuarios.
- Se debe implementar una infraestructura sin costo o de bajo costo para asegurar la sostenibilidad del proyecto.


<hr class="__chatgpt_plugin">

role::assistant

### No Funcionales

Como usuario del sistema
Quiero que el sistema sea compatible con Android, iPhone, Windows, Mac y Linux
Para poder acceder a la plataforma desde cualquier dispositivo o sistema operativo que utilice.

Como administrador del sistema 
Quiero que el software no dependa forzadamente de licencias de pago
Para minimizar los costos asociados al uso y mantenimiento del sistema.

Como usuario del sistema 
Quiero recibir actualizaciones uniformes en todos los dispositivos
Para asegurarme de tener siempre la última versión disponible sin importar desde qué dispositivo acceda al sistema.

Como líder de la fundación 
Necesito una infraestructura sin costo o de bajo costo para el despliegue del proyecto.
Para garantizar la sostenibilidad financiera a largo plazo.

<hr class="__chatgpt_plugin">

role::user

