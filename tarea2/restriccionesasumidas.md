// filepath: /Users/nicolaspereira/Downloads/restriccionesasumidas.txt

Restricciones asumidas para el sistema de reserva de exámenes (SE):

1. **Estructura de la solicitud de reserva:**

   - Un paciente puede solicitar varios exámenes en una misma solicitud.
   - Cada solicitud incluye un identificador único (`solicitudID`).
   - Los exámenes solicitados se identifican por un código único (`codigo`).

2. **Estructura de la respuesta de disponibilidad:**

   - La respuesta incluye el identificador de la solicitud (`solicitudID`) para correlacionar con la solicitud original.
   - Cada institución de salud tiene un identificador único (`codigo`) y un nombre (`nombre`).
   - Cada institución puede tener múltiples equipos disponibles para realizar los exámenes solicitados.
   - Los equipos se identifican por un código único (`id`).
   - La disponibilidad de cada equipo se expresa en fechas y horas específicas (`fechaHora`).

3. **Jerarquía de datos:**

   - La solicitud de reserva tiene una estructura jerárquica:
     - Solicitud -> Exámenes solicitados.
   - La respuesta de disponibilidad tiene una estructura jerárquica:
     - Respuesta -> Instituciones -> Equipos -> Disponibilidad.

4. **Restricciones de datos:**

   - Los códigos de exámenes, instituciones y equipos son cadenas alfanuméricas únicas.
   - Las fechas y horas deben seguir el formato ISO 8601 (`YYYY-MM-DDTHH:MM:SS`).
   - Los nombres de instituciones y exámenes son cadenas de texto.

5. **Flujo de información:**

   - El sistema SE envía una solicitud al MSP con los exámenes requeridos.
   - El MSP procesa la solicitud y responde con una lista de equipos disponibles.
   - El sistema SE muestra la información al usuario para que seleccione un equipo y confirme la reserva.

6. **Archivos necesarios:**

   - `examType.xsd`: Define el tipo de examen.
   - `institucionType.xsd`: Define la estructura de las instituciones.
   - `ubicationType.xsd`: Define la estructura de la ubicación de las instituciones.
   - `query.xml`: Define la estructura de la solicitud de reserva.
   - `response.xml`: Define la estructura de la respuesta de disponibilidad.
   - `queryexample.xml`: Ejemplo de solicitud de reserva.
   - `responseexample.xml`: Ejemplo de respuesta de disponibilidad.

7. **Validación:**

   - Los documentos XML deben ser validados contra sus respectivos esquemas XSD utilizando herramientas como Liquid XML Validator.
   - El formato de los documentos XML debe ser verificado con herramientas como FreeFormatter.

8. **Módulos del sistema:**
   - Módulo de solicitud: Genera y envía solicitudes de reserva al MSP.
   - Módulo de procesamiento: Procesa las solicitudes y genera respuestas de disponibilidad.
   - Módulo de visualización: Muestra la disponibilidad (debe ordenarla por horario) al usuario y permite confirmar la reserva.
