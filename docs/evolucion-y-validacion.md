# Evolución y validación del proyecto

[← Presentación](../README.md)

## Base documental

La reconstrucción se realizó a partir de la conversación **Retomar app de justificantes**, dentro del contexto de **Proyecto David**, y de los archivos locales de su entrega MENDOZIA 3.0.

Se revisaron MotorV3.gs, PanelV3.gs, panel3.html, MovilV3.gs, movil3.html, INSTALAR-V3.md y las pruebas locales de la entrega. El repositorio publica documentación; no incorpora automáticamente el código, los datos ni los recursos de la instalación institucional.

## Evolución funcional

| Etapa | Resultado del trabajo |
| --- | --- |
| Diseño inicial | Sustitución del recorrido de evidencias y avisos manuales por solicitudes en Forms y seguimiento en un mismo libro. |
| Primera automatización | Creación del libro y del formulario, catálogos, aviso al coordinador, decisiones y correos. Separación entre cuenta propietaria y coordinador. |
| Ajustes de operación | Fechas dentro de los 15 días naturales anteriores de lunes a viernes, observaciones, estados de envío y resolución protegida. |
| Presentación de correos | Fechas autorizadas explícitas para docentes y retroalimentación al alumno sobre días no autorizados. |
| Panel 2.0 | Calendario para selección de días, autorización parcial, confirmación y reenvío desde la interfaz. La casilla del libro queda informativa. |
| Mejoras de interfaz | Apertura automática del panel, carga al cambiar de fila, indicador de espera y capa de bloqueo durante una operación. |
| Identidad del producto | El nombre visible IRIS evoluciona a MENDOZIA; identificadores internos históricos se mantienen por compatibilidad. |
| Robustez de catálogos | Lectura por encabezados, columnas reordenables, conservación de ceros iniciales y validación de datos. |
| Recuperación y diagnóstico | Recuperación de respuestas faltantes, registro de errores, seguimiento de intentos y resolución de fallos. |
| Proceso único | Integración de recuperación, confirmaciones, correos y mantenimiento en cicloMendozia. |
| Versión 3.0 | Interfaz móvil en navegador, inicio de sesión, búsqueda, pendientes/resueltas y reutilización de la misma cola operativa. |
| Actualización de sincronización | Detección de cambios en grupos y alumnos, actualización automática de Forms, reintentos y resultado visible. |

La numeración histórica incluye revisiones 7.x antes del panel 2.0 y de la versión de producto 3.0. No debe interpretarse como una secuencia de tres sistemas distintos; la V3 conserva el protocolo y varios nombres de la instalación anterior.

## Comprobaciones realizadas para esta documentación

El **10 de noviembre de 2026** se ejecutaron ocho suites existentes en una copia local de la entrega, con servicios simulados y sin actuar sobre Google ni enviar correos reales.

| Suite | Cobertura principal | Resultado |
| --- | --- | --- |
| Motor | Orden de fases, bloqueo, cadencia, errores aislados y conservación de activadores ajenos. | Aprobada |
| Catálogos | Columnas movidas, grupo 0, ceros iniciales y encabezados inválidos. | Aprobada |
| Errores | Agrupación de fallos, resolución al recuperarse y conservación del error original. | Aprobada |
| Sincronización | Nuevos grupos/alumnos, detección de cambios, reintentos, grupos vacíos y reapertura de Forms tras fallo. | Aprobada |
| Recuperación | Lotes, respuestas antiguas, prevención de duplicados, aislamiento de errores y liberación de bloqueos. | Aprobada |
| Panel | Aprobación parcial, rechazo, privacidad de avisos, confirmación, reenvío y casilla informativa. | Aprobada |
| V3 | Identidad, acceso denegado, instalación reservada al propietario, búsquedas, bloqueo compartido y datos desactualizados. | Aprobada |
| Indicador de espera | Cambio de fila sin recargas repetidas, tratamiento de errores y retirada de la capa de espera. | Aprobada |

Los mensajes de error provocados deliberadamente por estas pruebas forman parte de sus casos de fallo; todas finalizaron correctamente.

## Evidencia de uso y límites de la revisión

En la conversación, el usuario confirmó el funcionamiento del flujo de computadora antes de solicitar el acceso móvil. También compartió ejecuciones reales de recuperación que finalizaron sin errores y posteriormente indicó que el sistema funcionaba como debía.

La conversación documenta la preparación y las pruebas locales de la web V3 y de la sincronización de catálogos. En esos puntos, la entrega original todavía pedía comprobar su publicación, la autorización de David y la actualización del formulario en la cuenta de Google.

Durante esta documentación no se volvió a verificar la instalación institucional ni qué versión está desplegada. Por tanto, los resultados locales acreditan el comportamiento probado del código de referencia, no una auditoría de todos los permisos o de la operación en producción.

## Alcance de la automatización

La revisión de evidencia y la autorización son decisiones del coordinador. El código revisado valida datos y automatiza el flujo, pero no contiene un modelo de IA que decida si debe otorgarse un justificante.

La gestión de seguridad combina los servicios institucionales de Google con los controles de cuenta y proceso implementados en el código. No se afirma que contratar la plataforma sustituya la configuración de permisos.

## Investigación y ejes

- **Líneas de investigación:** **PENDIENTES POR DEFINIR**
- **Ejes:** **PENDIENTES POR DEFINIR**
