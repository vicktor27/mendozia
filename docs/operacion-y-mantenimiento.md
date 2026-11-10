# Operación y mantenimiento

[← Presentación](../README.md)

## Accesos y perfiles

Las URLs operativas se distribuyen por los canales institucionales y se omiten de esta documentación pública.

| Perfil | Uso |
| --- | --- |
| Alumno | Presentar la solicitud en el formulario con su cuenta institucional y adjuntar evidencia. |
| Coordinador | Revisar evidencia, autorizar o rechazar, confirmar y consultar el seguimiento. |
| Propietario técnico | Administrar el libro, los scripts, los activadores y los permisos de la instalación. |

En el proyecto del motor, la hoja **Configuración** conserva ENLACE_ALUMNOS, ENLACE_EXCEL y EDITAR_FORMULARIO. La URL móvil se obtiene en la implementación del proyecto vinculado al libro. Estos valores no se trasladan al repositorio.

## Revisión de una solicitud

1. Abrir el libro y su panel MENDOZIA, o la aplicación móvil con una cuenta autorizada.
2. En computadora, seleccionar una fila de **Solicitudes**. En móvil, buscar por alumno, matrícula, grupo o folio y abrir el caso.
3. Revisar la validación y la evidencia.
4. Elegir los días autorizados, o seleccionar rechazo y escribir las observaciones.
5. Pulsar **Confirmar** una vez y seguir el estado de la operación.

La web permite consultar pendientes y resueltas, con páginas de hasta 30 registros. Mientras una confirmación está en proceso, la interfaz consulta su estado; el trabajo confirmado continúa aunque se cierre el navegador.

Las modificaciones sin confirmar permanecen en la pantalla y se descartan al volver a la lista móvil. Una resolución guardada queda protegida; reenviar es una acción distinta.

## Interpretación de los estados

| Presentación | Significado |
| --- | --- |
| Pendiente de revisión | Todavía no se ha confirmado una resolución. |
| Confirmación recibida / En cola | La orden fue registrada y espera procesamiento. |
| Procesando | El motor está atendiendo la resolución o sus avisos. |
| Autorizada o Rechazada con avisos pendientes | La decisión existe, pero falta completar los envíos. |
| Completado | Todos los avisos esperados fueron aceptados por el servicio de correo. |
| Requiere revisión | Existe un fallo o un resultado que necesita atención. |

**Enviado no significa leído ni entregado en bandeja de entrada.** La implementación registra la aceptación del envío por Google; no comprueba aperturas, spam ni rebotes posteriores.

Ante un resultado incierto, revisar **Envíos** antes de solicitar otro intento. Los registros Error, Revisar o Enviando no confirmado no se reenvían ciegamente: el sistema ofrece reenvío explícito para evitar duplicados.

## Proceso programado único

**cicloMendozia** ordena las fases:

1. Recuperar respuestas que falten en Solicitudes.
2. Procesar las confirmaciones y los reenvíos.
3. Atender los correos pendientes.
4. Ejecutar mantenimiento cuando corresponda.

La instalación lo programa aproximadamente cada minuto. El mantenimiento se intenta aproximadamente cada cinco minutos, condicionado al trabajo pendiente y al tiempo disponible. Son cadencias de procesamiento, no promesas de ejecución en segundos exactos.

Se conserva un bloqueo del motor para evitar concurrencia con otras entradas. Si está ocupado, el trabajo permanece pendiente. La activación sustituye únicamente los relojes anteriores de MENDOZIA y conserva activadores ajenos.

## Alta de grupos y alumnos

Mantener los encabezados de **Grupos**, **Alumnos** y **Maestros**, con matrículas, grupos y correos válidos. El código lee todas las filas con datos; no fija un número predeterminado de grupos.

Con la sincronización automática activada:

- El catálogo de Grupos es la referencia.
- Solo se publican en Forms los grupos con alumnos válidos.
- Los grupos vacíos se informan en RESULTADO_ACTUALIZACION.
- Una huella del catálogo evita reconstruir Forms si nada cambió.
- Los fallos conservan un reintento pendiente y se registran en la hoja de errores.
- Si la actualización interrumpe un formulario abierto, el reintento correcto puede reabrirlo; uno previamente cerrado conserva ese estado.

La lectura dinámica no elimina el límite preventivo de **290 elementos** del diseño del formulario. Las secciones históricas se conservan para mantener identificadores, por lo que el crecimiento puede requerir revisar la estructura.

## Diagnóstico y recuperación

| Incidencia | Revisión |
| --- | --- |
| Un grupo no aparece en Forms | Comprobar que existe en Grupos, que tiene alumnos válidos y el resultado de la última sincronización. |
| Hay respuesta en Forms pero no en Solicitudes | Revisar catálogos y Errores MENDOZIA. El proceso único recupera respuestas faltantes por su identificador, sin pedir automáticamente otro envío al alumno. |
| Se muestra proceso ocupado | Revisar ejecuciones del motor y dejar que el ciclo vuelva a intentarlo; no confirma por sí mismo una pérdida de datos. |
| Faltan avisos | Consultar los registros por destinatario en Envíos y el resultado de la resolución. |
| Acceso denegado al coordinador | Revisar la cuenta conectada, las dos cuentas autorizadas, los permisos del libro y la configuración de ejecución de la web. |
| Evidencia inaccesible | Revisar con la cuenta autorizada los permisos de Drive, sin convertir el archivo en público. |

La hoja de errores agrupa fallos pendientes por proceso y referencia, actualiza el número de intentos y los marca como resueltos al recuperarse. No se deben borrar registros para simular que una operación terminó.

## Actualización de una instalación existente

La entrega V3 supone que el panel anterior y el proceso único ya están instalados. No es una instrucción para regenerar el formulario ni iniciar otra instalación.

| Cambio | Acción prevista en la guía original |
| --- | --- |
| Motor V3 | Reemplazar el código del motor por MotorV3.gs y ejecutar actualizarVersion3 con la cuenta propietaria. |
| Panel y móvil | En el proyecto vinculado al libro, reemplazar el panel con PanelV3.gs y panel3.html; agregar MovilV3.gs y movil3.html. Ejecutar configurarVersion3. |
| Publicación móvil | Publicar desde el proyecto vinculado al libro, como usuario que accede y para la organización. |
| Sincronización de catálogos | Con el proceso único activo, actualizar el motor y ejecutar activarSincronizacionFormularioV3. No requiere republicar la web. |

No conservar dos copias de las mismas funciones. Para actualizar una web ya publicada, editar la implementación existente y seleccionar una nueva versión permite conservar su URL; guardar código por sí solo no actualiza la versión publicada.

La instalación y las autorizaciones en Google deben realizarlas las cuentas correspondientes. Esta documentación no ejecutó esos pasos ni modificó la instalación real.
