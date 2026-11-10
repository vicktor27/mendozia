# MENDOZIA IA · Gestión de justificantes académicos

**Proyecto impulsado por el MAE David Rodríguez Ceballos, desarrollado con la colaboración del Dr. Víctor Manuel Solís Cardoza.**

## Presentación

MENDOZIA IA es la evolución del trabajo iniciado como **Proyecto David**: una solución para recibir, revisar y resolver solicitudes de justificantes académicos mediante las herramientas de Google que la institución ya tiene contratadas.

El proceso original requería que el alumno presentara su evidencia al coordinador y que este notificara manualmente a los docentes. El sistema integra la captura de la solicitud, la revisión de evidencias, la autorización de días y las notificaciones por correo en un mismo flujo.

**La decisión de autorizar o rechazar corresponde al coordinador.** MENDOZIA automatiza el registro, las validaciones y las comunicaciones.

## Participantes

| Participante | Participación |
| --- | --- |
| **MAE David Rodríguez Ceballos** — Maestro en Educación | Principal impulsor del proyecto |
| **Dr. Víctor Manuel Solís Cardoza** | Colaborador en el desarrollo del proyecto |

## Funcionamiento general

1. El alumno presenta su solicitud en **Google Forms**, con su grupo, registro del catálogo, días solicitados, motivo y evidencia.
2. Las respuestas se conservan en **Google Sheets** y el motor registra la solicitud con un folio.
3. El coordinador recibe un aviso y revisa la evidencia desde el panel de computadora o la interfaz móvil desarrollada para la versión 3.
4. Selecciona los días que autoriza, o rechaza la solicitud con observaciones, y pulsa **Confirmar**.
5. El proceso automático registra la resolución y atiende los avisos por correo: una autorización notifica al alumno y a los docentes configurados; un rechazo se comunica al alumno.

## Funciones desarrolladas

- Catálogos de grupos, alumnos y docentes, leídos por encabezados y sin rangos fijos de filas.
- Selección de días mediante calendario en el panel y aprobación total o parcial.
- Evidencias en Drive con acceso del coordinador; los avisos docentes no incluyen evidencia ni motivo privado.
- Confirmación explícita, decisiones protegidas y reenvíos deliberados.
- Estados visuales y registro por destinatario en **Envíos**.
- Recuperación de respuestas faltantes y control de solicitudes duplicadas.
- Proceso programado único **cicloMendozia**.
- Diagnóstico en **Errores MENDOZIA**, compatible con el nombre anterior **Errores Mendoza**.
- Sincronización automática de grupos y alumnos con el formulario.
- Interfaz web móvil con búsqueda y separación entre solicitudes pendientes y resueltas.

## Plataforma y seguridad

La entrega revisada utiliza **Google Forms, Google Sheets, Google Drive y Google Apps Script**, con interfaces HTML para computadora y móvil.

**La infraestructura, la autenticación y los permisos base se apoyan en las herramientas de Google ya contratadas por la institución.** El código complementa esos controles al comprobar, en cada operación del panel y la web, que la cuenta corresponda al propietario o al coordinador.

Los permisos de Drive, los del libro y la configuración de publicación siguen formando parte de la administración institucional. [Consultar arquitectura y seguridad](docs/funcionamiento-y-arquitectura.md).

## Documentación

- [Funcionamiento, reglas, arquitectura y seguridad](docs/funcionamiento-y-arquitectura.md).
- [Operación, mantenimiento y solución de incidencias](docs/operacion-y-mantenimiento.md).
- [Evolución del proyecto y validación](docs/evolucion-y-validacion.md).

## Accesos al sistema

Las URLs del formulario, del libro de control y de la aplicación móvil **no se publican por indicación de los participantes**. Su distribución se mantiene en los canales institucionales autorizados.

## Estado del proyecto

**Proyecto desarrollado. Entrega de referencia: MENDOZIA 3.0**, con la actualización de sincronización de catálogos.

Esta documentación se elaboró a partir de la conversación de desarrollo, los archivos de la entrega y ocho suites locales ejecutadas el **10 de noviembre de 2026**. Describe el código revisado; no sustituye la comprobación de la versión y los permisos desplegados en Google.

## Líneas de investigación y ejes

- **Líneas de investigación:** **PENDIENTES POR DEFINIR**
- **Ejes:** **PENDIENTES POR DEFINIR**
