# Checkpoint 1 — BPMN AS-IS + Oportunidades de Automatización

**INF 320 Automatización de Procesos de Negocios · Semestre 2026-2**  
**Entrega:** Semana 5 · **Peso:** 15% del proyecto integrador  

---

## Datos del equipo

| Campo | Información |
| :--- | :--- |
| **Equipo** | Panamá Tech Solutions (Modalidad Individual - Faris De Pasquale) |
| **Negocio** | Panamá Tech Store (E-commerce minorista de hardware, periféricos y accesorios) |
| **Proceso intervenido** | Proceso de Devolución de Pedido y Garantía Postventa |
| **Versión del entregable** | v1.0 |

---

## 1. Diagrama BPMN AS-IS

### Descripción del proceso (en palabras, antes de ver el diagrama)

El flujo operativo actual se ejecuta a través de 8 pasos distribuidos entre tres áreas funcionales:

| Paso | Actor | Descripción | Tiempo aproximado |
| :---: | :--- | :--- | :---: |
| **1** | Cliente | Detecta falla de hardware o inconformidad y llena el formulario web/WhatsApp adjuntando evidencias fotográficas y comprobante. | 10 min |
| **2** | Atención al Cliente | Descarga y analiza visualmente las fotos; valida si el reclamo cumple las condiciones generales de garantía. Si no procede, notifica el rechazo. | 20 min |
| **3** | Atención al Cliente | Ingresa manualmente al portal del courier local, transcribe datos de retiro y genera la guía de retorno para el cliente. | 15 min |
| **4** | Cliente / Courier | El cliente entrega el paquete en sucursal o courier retira a domicilio; traslado logístico hacia la bodega central. | 24 - 48 horas |
| **5** | Logística / Almacén | Recibe el paquete, desempaca, coteja número de serie y realiza pruebas técnicas en banco de hardware para verificar el daño. | 35 min |
| **6** | Logística / Almacén | Si la inspección es conforme, registra manualmente el ingreso del SKU devuelto en la hoja de cálculo de inventario. | 10 min |
| **7** | Atención al Cliente | Tras recibir aviso verbal o por chat del almacén, accede a banca en línea o Yappy comercial para procesar el reembolso monetario. | 15 min |
| **8** | Atención al Cliente | Redacta correo de confirmación de cierre, adjunta el comprobante de transferencia y finaliza el caso. | 5 min |

---

### Diagrama BPMN AS-IS

Los archivos fuente y de visualización vectorial se encuentran vinculados en el repositorio:

* **Diagrama (formato vectorial nítido):** `../../diagramas/bpmn-as-is-v1.svg` (también disponible en `../kickoff/diagrama-as-is-practica.svg`)
* **Modelo editable BPMN 2.0:** `../../diagramas/bpmn-as-is-v1.bpmn` (también disponible en `../kickoff/diagrama-as-is-practica.bpmn`)

---

### Indicadores operativos actuales (medidos o estimados)

| Indicador | Valor actual |
| :--- | :--- |
| **Frecuencia del proceso** | 12 a 18 solicitudes por semana |
| **Tiempo promedio por ejecución (Lead Time)** | 4.2 días hábiles (~100 horas totales transcurridas) |
| **Tiempo de trabajo manual activo (Touch Time)** | ~110 minutos por caso gestionado |
| **Tasa de error aproximada** | 14% de casos con retrasos por datos bancarios mal digitados o stock no actualizado |
| **Número de actores involucrados** | 3 actores (Cliente, Agente de Atención, Operador de Almacén) |

---

## 2. Cuellos de botella identificados

| Cuello de botella | Paso afectado | Impacto estimado |
| :--- | :--- | :--- |
| **Punto ciego y desincronización entre Almacén y Atención** | Paso 5 a Paso 7 | Los artículos quedan inspeccionados pero no se notifica a administración de inmediato, generando 24 a 48 horas de retraso pasivo en el reembolso. |
| **Transcripción manual repetitiva de datos** | Paso 3 y Paso 7 | Errores humanos en direcciones para el courier y en números de cuenta bancaria/Yappy, causando rechazos de pago y retrabajo. |
| **Triaje manual de evidencias fotográficas** | Paso 2 | Demoras de hasta 24 horas en responder al cliente por acumulación de correos y consultas no estructuradas. |

---

## 3. Oportunidades de automatización identificadas

| Oportunidad | Descripción | Pasos del proceso que afecta |
| :--- | :--- | :--- |
| **Op. 1: Validación y generación automática de guías** | Capturar datos del formulario y disparar la orden de recolección en el courier mediante webhook/API, enviando la etiqueta PDF al cliente de inmediato. | Pasos 2 y 3 |
| **Op. 2: Sincronización y disparador automático de reembolso** | Crear un formulario interno digital para Logística que, al marcar la inspección como "Aprobada", actualice el inventario y alerte a Atención con los datos de pago listos. | Pasos 5, 6 y 7 |
| **Op. 3: Notificación multicanal automatizada y cierre** | Disparar correos automáticos al cliente en cada cambio de estado (recibido en bodega, en inspección, reembolso emitido). | Pasos 4, 7 y 8 |
| **Op. 4: Chatbot de triaje y preclasificación con IA** | Asistente virtual en WhatsApp/web que valide número de pedido, consulte vigencia de compra y solicite fotos con requerimientos obligatorios. | Paso 1 y 2 |

---

## 4. Matriz de priorización

| Oportunidad | Volumen (1-5) | Repetitividad (1-5) | Reglas claras (1-5) | Valor (1-5) | Esfuerzo (Bajo/Medio/Alto) | Puntaje total |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Op. 2: Sincronización Almacén-Inventario-Reembolso** | 4 | 5 | 5 | 5 | **Bajo** | **19** |
| **Op. 3: Notificación multicanal de estados** | 5 | 5 | 5 | 4 | **Bajo** | **19** |
| **Op. 1: Generación automática de guías courier** | 4 | 4 | 4 | 4 | **Medio** | **16** |
| **Op. 4: Chatbot de triaje con IA conversacional** | 4 | 3 | 3 | 4 | **Alto** | **14** |

---

## 5. Oportunidad seleccionada para el proyecto

* **Oportunidad elegida:** **Sincronización digital Almacén-Inventario y disparador de Reembolso (Op. 2) combinada con Notificaciones automáticas al cliente (Op. 3)**.
* **Justificación:** Representa el mayor "Quick Win" del proceso. Obtuvo 19 puntos con esfuerzo de implementación bajo-medio en plataformas como Make/n8n/Zapier. Elimina el principal cuello de botella operativo (el silencio informativo entre la bodega y finanzas) mediante reglas de decisión deterministas (*if inspección == aprobada then actualizar inventario y alertar pago*).
* **Impacto esperado:**
  - Reducción del tiempo de ciclo de reembolso de 4.2 días a menos de 24 horas tras la llegada física a bodega.
  - Eliminación completa (0%) de discrepancias entre inventario físico y stock web para artículos devueltos aptos.
  - Reducción del 80% de mensajes de clientes consultando "¿cómo va mi reembolso?".

---

## 6. ¿Qué sigue? (Plan hacia el Checkpoint 2)

Durante las próximas 4 semanas (Módulo 3: Diseño e Implementación TO-BE):
- **Tarea 1 (Semana 6):** Modelar el diagrama BPMN TO-BE integrando compuertas lógicas, eventos de mensaje y tareas de servicio automatizadas.
- **Tarea 2 (Semana 7):** Configurar el flujo de integración en plataforma de automatización (Make/n8n), conectando el formulario digital de almacén con Google Sheets y disparadores de correo.
- **Tarea 3 (Semana 8):** Probar el flujo completo con datos simulados (happy path y caminos de rechazo) y documentar evidencias para el Checkpoint 2.

---

## Declaración de uso de IA

| Campo | Detalle |
| :--- | :--- |
| **¿Se usó IA?** | Sí |
| **Herramienta(s)** | Gemini 2.5 Flash |
| **Para qué se usó** | Para estructurar la matriz de priorización ponderada, redactar la justificación técnica de los criterios y organizar las tablas conforme a la rúbrica oficial de la Semana 5. |
| **Qué hizo el equipo por su cuenta** | Levantamiento de la información operativa de Panamá Tech Store, estimación de métricas de tiempos/errores, modelado del diagrama AS-IS en bpmn.io y selección estratégica del cuello de botella a intervenir. |
