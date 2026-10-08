# Ficha de Equipo — Kickoff del Proyecto Integrador

**INF 320 Automatización de Procesos de Negocios · Semestre 2026-2**  
*Completar en la Semana 3*

---

## Datos del equipo

| Campo | Información |
| :--- | :--- |
| **Nombre del equipo** | Panamá Tech Solutions |
| **Integrante 1** | Faris De Pasquale · Cédula: 8-1029-65 · Email: depasuqalef16@gmail.com |


---

## Negocio elegido

| Campo | Información |
| :--- | :--- |
| **Nombre del negocio** | Panamá Tech Store |
| **Tipo de negocio** | Tienda virtual de comercio electrónico orientada a la venta minorista de componentes de computadoras, periféricos y accesorios tecnológicos. |
| **¿Real o simulado?** | Simulado (basado en dinámicas reales de comercio local panameño) |
| **Si es real: consentimiento del propietario** | No aplica (modelo simulado con fines estrictamente académicos) |
| **Canal(es) de venta** | Sitio web propio y canal de atención/cierre de ventas por WhatsApp |

---

## Proceso a intervenir

| Campo | Información |
| :--- | :--- |
| **Nombre del proceso** | Proceso de Devolución de Pedido y Garantía |
| **Descripción breve** | El proceso gestiona las solicitudes de devolución de clientes por fallas o inconformidad, verificando fotos de evidencia, coordinando la recepción física del producto en bodega para inspección técnica y ejecutando el reembolso económico si procede. Se ejecuta bajo demanda cada vez que un cliente reporta una incidencia postventa. |
| **Actor(es) involucrado(s)** | Cliente, Atención al Cliente, Logística / Almacén. |
| **Problema principal que tiene hoy** | Todo el triaje se realiza manualmente por chat y correo; la revisión física en almacén no está sincronizada con administración, lo que ocasiona demoras de hasta 4 a 6 días hábiles para responder o emitir un reembolso, generando reclamos y retrabajo en inventario. |
| **¿Por qué es relevante automatizarlo?** | Estandariza la validación inicial de solicitudes, reduce drásticamente el tiempo de ciclo en las devoluciones, evita errores en el inventario de reingreso y mejora la confianza del cliente en las compras online. |

---

## Distribución provisional de roles

| Integrante | Área de responsabilidad provisional |
| :--- | :--- |
| **Faris De Pasquale** | **BPMN y análisis del proceso** (diseño y documentación de flujos AS-IS y TO-BE). |
| **Faris De Pasquale** | **Automatización (Zapier/Make/n8n)** (lógica de integración entre formularios y notificaciones). |
| **Faris De Pasquale** | **Chatbot/IA conversacional** (captura inicial de datos de devolución e incidencias). |
| **Faris De Pasquale** | **Marketing automation y KPIs** (medición de tiempos de resolución y satisfacción). |
| **Faris De Pasquale** | **Seguridad, documentación y coordinación** (gestión del repositorio GitHub y control de versiones). |


---

## Declaración de integridad académica

Declaro que:
1. Este proyecto es un negocio simulado creado para fines académicos, modelado a partir de prácticas operativas comunes en el e-commerce local.
2. Los datos de clientes utilizados son completamente ficticios y anonimizados.
3. El uso de herramientas de IA generativa está declarado explícitamente a continuación.
4. Comprendo y aplico la política de integridad académica del curso.

**Firma:** Faris De Pasquale

---

## Declaración de Uso de IA y Trazabilidad de Prompts

Para estructurar la ficha de kickoff, delimitar los límites del proceso y validar la consistencia del diagrama BPMN 2.0, se utilizó asistencia de inteligencia artificial mediante el siguiente flujo secuencial:

* **Prompt 1 (Exploración del caso):** *"Necesito plantear un caso de estudio individual de automatización de procesos para una tienda online en Panamá. ¿Qué proceso postventa suele presentar mayores demoras manuales y problemas de coordinación entre atención y bodega?"*
* **Prompt 2 (Estructuración del flujo y actores):** *"Voy a modelar el proceso de Devolución de Pedido. Define qué carriles (Lanes) debe tener para BPMN 2.0 y cuáles son los dos puntos críticos de decisión (compuertas exclusivas) que deben validarse antes del reembolso."*
* **Prompt 3 (Adaptación a plantilla y roles individuales):** *"Adapta la plantilla oficial de kickoff del curso INF 320 para un único integrante, justificando la asunción de todos los roles técnicos y organizando las respuestas en las tablas requeridas."*

---

## Archivos Adjuntos del Modelado BPMN
* **Diagrama (formato vectorial SVG):** `proyecto-integrador/kickoff/diagrama-as-is-practica.svg`
* **Modelo fuente (BPMN 2.0 XML):** `proyecto-integrador/kickoff/diagrama-as-is-practica.bpmn`
