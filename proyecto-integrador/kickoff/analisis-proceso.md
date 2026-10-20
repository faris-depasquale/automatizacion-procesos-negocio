# Laboratorio 2 — Documento de Análisis del Proceso (AS-IS)

**INF 320 Automatización de Procesos de Negocios · Semestre 2026-2**  
**Módulo 2:** Herramientas, diseño e implementación de procesos automatizados  
**Semana 4**  

* **Estudiante:** Faris De Pasquale  
* **Empresa / Negocio:** Panamá Tech Store (Comercio electrónico de periféricos y componentes tecnológicos)  
* **Proceso evaluado:** Proceso de Devolución de Pedido y Garantía  
* **Modalidad:** Trabajo individual  

---

## 1. Guía de Preguntas para la Entrevista de Análisis de Proceso

**Técnica aplicada:** Entrevista semiestructurada al responsable operativo del proceso.  
**Entrevistado:** Encargado de Atención al Cliente y Postventa (Simulado)  
**Entrevistador:** Faris De Pasquale  

### Sobre el Proceso

**1. ¿Puedes describir el proceso paso a paso desde que inicia hasta que termina?**  
> El proceso inicia cuando el cliente detecta una anomalía o falla en su componente y llena el formulario de devolución adjuntando fotos del estado del producto y del comprobante. Atención al Cliente recibe esa información y hace una primera revisión visual; si no procede según la política de garantía, se notifica el rechazo al cliente y termina. Si procede, generamos manualmente una guía de retorno y coordinamos con el courier para que recoja el paquete o el cliente lo entregue.  
> Cuando el producto llega a nuestra bodega física, el auxiliar de Logística/Almacén lo recibe, abre el paquete e inspecciona técnicamente el hardware. Si el daño fue por mal uso o alteración, se rechaza la garantía y se cancela la devolución. Si el estado es conforme, se reingresa el artículo al inventario disponible, se escala la notificación interna a Atención al Cliente para que emita el reembolso por banca en línea o Yappy, y finalmente se le envía el comprobante al cliente por correo electrónico, concluyendo el flujo con éxito.

**2. ¿Quiénes intervienen en el proceso? (roles, sistemas, departamentos)**  
* **Roles humanos:** Cliente final, Agente de Atención al Cliente y Auxiliar de Logística/Almacén.  
* **Sistemas y herramientas:** Google Forms / WhatsApp Business (recepción de reportes), correo electrónico institucional, hoja de cálculo de Google Sheets / Excel (control de inventario), portal web del courier local para guías y portal de banca en línea (banca corporativa para transferencias ACH y Yappy Comercial).  
* **Departamentos:** Postventa / Servicio al Cliente y Logística / Operaciones de Almacén.

**3. ¿Con qué frecuencia ocurre este proceso? (diario, semanal, por pedido)**  
> Se ejecuta bajo demanda cada vez que un comprador reporta un problema. En promedio manejamos un volumen de **12 a 18 solicitudes de devolución o reclamo de garantía por semana**, aumentando en semanas posteriores a campañas de promociones o descuentos.

**4. ¿Cuánto tiempo toma desde el inicio hasta el fin en promedio?**  
> El tiempo de ciclo total promedia **entre 3 y 5 días hábiles** (alrededor de 72 a 120 horas transcurridas). La mayor parte de ese tiempo se diluye en el traslado físico del paquete por mensajería y en los tiempos muertos de espera en almacén para la revisión técnica.

---

### Sobre los Problemas

**5. ¿Cuáles son los pasos que más tiempo consumen? ¿Por qué?**  
> Dos pasos consumen la mayor parte del tiempo:  
> 1. **La inspección técnica en Logística/Almacén:** Los paquetes recibidos suelen apilarse en una zona de espera temporal y pueden tardar de 24 a 48 horas hábiles antes de ser evaluados exhaustivamente.  
> 2. **La revisión inicial de fotos y comprobantes:** Cuando el cliente envía imágenes con baja resolución o sin número de serie visible, Atención al Cliente debe iniciar un intercambio manual de mensajes que dilata la aprobación de la guía de retorno.

**6. ¿En qué pasos se cometen errores con más frecuencia?**  
> En la transcripción de datos bancarios para el reembolso (errores de un dígito en cuentas de banco que rebotan el pago) y en la falta de registro inmediato en la hoja de inventario cuando el almacén declara el producto como apto, lo que genera descuadres entre el stock físico y el mostrado en la tienda web.

**7. ¿Hay pasos que se hacen manualmente que podrían automatizarse?**  
* La validación de datos iniciales del formulario y confirmación de recepción de solicitud.  
* La generación automatizada de la guía de retorno del courier mediante integración API/webhook.  
* La notificación interna automática entre Logística y Atención una vez completada la inspección física.  
* La actualización directa del stock devuelto en el catálogo del e-commerce.  
* El envío automatizado del comprobante de reembolso y cierre del ticket por correo electrónico.

**8. ¿Alguna vez el proceso "se atasca"? ¿En qué punto?**  
> Sí, se atasca de forma recurrente en el **traspaso de información entre Logística y Atención al Cliente**. Almacén concluye la inspección favorablemente pero no envía la confirmación inmediata a soporte administrativo, dejando el reembolso en pausa durante días hasta que el cliente reclama por WhatsApp.

---

### Sobre los Datos

**9. ¿Qué información se genera en cada paso? (formularios, emails, hojas de cálculo)**  
* **Paso 1 (Solicitud):** ID de orden, cédula del comprador, correo, motivo de devolución, fotos del producto y foto de la factura digital.  
* **Paso 2 (Triaje inicial):** Estado de pre-aprobación y observaciones del agente.  
* **Paso 3 (Guía):** Código de rastreo (tracking number) generado en PDF o enlace del operador logístico.  
* **Paso 4 (Inspección física):** Diagnóstico técnico de conformidad (Aprobado/Rechazado) y causal de falla.  
* **Paso 5 (Reingreso):** Registro de SKU devuelto, fecha y nuevo saldo en el inventario de stock.  
* **Paso 6 (Reembolso y comprobante):** Número de transacción bancaria / referencia Yappy y correo final con adjunto de comprobante contable.

**10. ¿Cómo se comunican los diferentes actores del proceso? (email, WhatsApp, sistema)**  
> Con el cliente la comunicación es mixta (WhatsApp Business y correo). La coordinación interna entre el personal de almacén y atención se realiza de forma desestructurada mediante chats internos de WhatsApp y notas adhesivas colocadas sobre los paquetes físicos en bodega, sin un software de gestión unificado.

---

## 2. Registro de Observación Directa (Walkthrough)

## Registro de Observación — Proceso de Devolución de Pedido y Garantía

**Fecha:** 8 de octubre de 2026  
**Observador(es):** Faris De Pasquale  
**Negocio / Proceso:** Panamá Tech Store / Devolución de Pedido y Garantía  

| Paso | Actor | Tiempo aproximado | Sistema/Herramienta | Observaciones |
| :--- | :--- | :--- | :--- | :--- |
| **1. Llenar formulario de devolución** | Cliente | 8 - 12 min | Formulario Web / WhatsApp | El cliente requiere asistencia si no sabe localizar el número de serie de la pieza o extravió la factura. |
| **2. Revisar solicitud y fotos** | Atención al Cliente | 15 - 25 min | Correo / WhatsApp Web / Drive | Validación visual manual; el agente descarga y coteja las fotos contra la base de datos de pedidos vendidos. |
| **3. Generar guía de retorno** | Atención al Cliente | 10 - 15 min | Portal web de mensajería | Copia y pega de datos personales y dirección de retiro; paso altamente susceptible a errores de tipeo. |
| **4. Entregar producto al courier** | Cliente / Courier | 24 - 48 horas | Courier logístico local | Tiempo pasivo de traslado; sujeto a la disponibilidad del cliente en domicilio o visita a sucursal. |
| **5. Recibir e inspeccionar producto** | Logística / Almacén | 25 - 40 min | Banco de pruebas / Formato físico | Revisión de precintos de garantía y prueba eléctrica/funcional. Se acumula cuando hay poco personal. |
| **6. Reingresar producto a inventario** | Logística / Almacén | 5 - 10 min | Google Sheets / Excel | Ajuste manual del número de unidades disponibles del SKU correspondiente. |
| **7. Emitir reembolso al cliente** | Atención al Cliente | 10 - 20 min | Banca en Línea / Portal Yappy | El operador ingresa a la plataforma bancaria, transcribe número de cuenta o teléfono y ejecuta el desembolso. |
| **8. Enviar comprobante por correo** | Atención al Cliente | 5 min | Correo institucional | Generación manual del correo, adjuntando la captura de la banca en línea y notificando el fin del caso. |

---

### Cuellos de Botella Identificados:
* **Brecha de sincronización entre Almacén y Atención:** Ausencia de un disparador digital inmediato que notifique a Atención cuando Almacén aprueba la inspección técnica.
* **Transcripción manual repetitiva:** Redundancia en el ingreso de datos entre el formulario, la plataforma de envíos del courier y la banca en línea, elevando el riesgo de errores operativos.
* **Falta de visibilidad del estado para el cliente:** El usuario no cuenta con un sistema de consulta en tiempo real sobre la fase en que se encuentra su paquete devuelto o su reembolso, saturando el canal de WhatsApp con consultas de seguimiento.

---

### Datos Operativos Estimados:
* **Frecuencia del proceso:** 12 a 18 solicitudes por semana.  
* **Tiempo total promedio (Lead Time):** 4.2 días hábiles (~100 horas acumuladas).  
* **Tiempo de trabajo manual activo (Touch Time):** ~75 a 125 minutos de labor humana directa por cada solicitud resuelta.  
* **Tasa de error aproximada:** 14% (principalmente retrasos por transcripción incorrecta de datos bancarios o discrepancias en la actualización manual de inventario).  

---

## 3. Declaración de Integridad y Trazabilidad de Prompts

Declaro que este documento constituye un análisis operativo individual correspondiente a la Semana 4 del curso INF 320, basado en un modelo simulado verosímil del comercio electrónico panameño.

**Prompts de IA utilizados:**
1. *"Con base en el diagrama AS-IS modelado para Panamá Tech Store, redacta las respuestas a las 10 preguntas estándar de la entrevista al dueño del proceso, justificando tiempos de ciclo, herramientas y causas de atraso."*
2. *"Completa la plantilla oficial de observación directa (walkthrough) desglosando los 8 pasos del proceso, los sistemas utilizados, los cuellos de botella y los indicadores operativos requeridos."*

