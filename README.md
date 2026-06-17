# 🧪 QA Portfolio — Roberto Ruiloba

QA Engineer | API Testing | Functional Testing | Jira

QA Engineer con experiencia práctica en pruebas funcionales, pruebas de API REST y reporte de defectos, formado a través del bootcamp intensivo de TripleTen.

Durante mis proyectos, diseñé y ejecuté más de 100 casos de prueba utilizando técnicas como clases de equivalencia, análisis de valores límite y pruebas de regresión. También documenté y gestioné incidencias en Jira, identificando defectos tanto en aplicaciones web como en APIs.

🔧 Tecnologías y herramientas

• Postman
• APIs REST
• HTTP Status Codes
• JSON Validation
• Jira
• Test Case Design
• Equivalence Classes & Boundary Value Analysis
• Regression Testing
• Cross-Browser Testing
• Agile / Scrum

📌 Mi objetivo es contribuir a la calidad del software mediante pruebas efectivas, identificación temprana de defectos y mejora continua de la experiencia del usuario.

Actualmente busco oportunidades como QA Engineer o QA Tester donde pueda seguir desarrollando mis habilidades y aportar valor a equipos de desarrollo enfocados en la calidad.


# Proyectos QA — Roberto Ruiloba

Documentación de los 3 proyectos desarrollados durante el bootcamp de QA en TripleTen, sobre la aplicación **Urban Routes** (servicio de transporte tipo ride-sharing). Cada proyecto cubre una fase distinta del ciclo de pruebas: diseño de casos, ejecución de checklists UI y pruebas de API.

---

## 📁 Proyecto 1 — Diseño de Casos de Prueba: Clases de Equivalencia y Valores Límite

### Objetivo
Diseñar casos de prueba para validar el formulario de registro de pasajero (campos Nombre y Apellido) y el cálculo de tiempo/costo de viaje según la hora de salida, usando técnicas formales de diseño de pruebas.

### Herramientas utilizadas
Hojas de cálculo (Excel/Google Sheets) para documentación de clases de equivalencia y casos de prueba.

### Qué hice
Aplicé dos técnicas clásicas de QA para encontrar el máximo de defectos con el mínimo de casos:

**Clases de equivalencia** sobre los campos Nombre y Apellido, cubriendo 26 escenarios distintos: longitud válida (2-14 caracteres), longitud insuficiente, longitud excesiva, letras con guión, letras con espacio, números inválidos, campos vacíos, caracteres especiales, caracteres no latinos (ñ) y caracteres con acento.

**Análisis de valores límite** sobre la lógica de cálculo de viaje, validando 5 franjas horarias (00:01-08:00, 08:01-12:00, 12:01-18:00, 18:01-22:00, 22:01-00:00), cada una con una velocidad distinta que afecta el cálculo de tiempo y costo.

### Casos de prueba ejecutados
6 casos de prueba funcionales verificando que el sistema calculara correctamente la duración y el costo de un viaje compartido según la hora de salida, incluyendo el caso límite de origen y destino idénticos (resultado esperado: 0 km, $0).

### Resultado
Documentación completa que sirve como base de regresión: cualquier cambio futuro en el algoritmo de tarifas puede validarse contra estos 6 casos sin necesidad de rediseñarlos.

### Tecnologías / Conceptos aplicados
`Equivalence Partitioning` · `Boundary Value Analysis` · `Functional Testing` · `Test Case Design`

---

## 📁 Proyecto 2 — Pruebas de UI: Checklists Cross-Browser y Casos de Prueba Funcionales

### Objetivo
Validar el flujo completo de reserva de un vehículo en Urban Routes —desde la selección de tarifa hasta la confirmación de reserva— en dos navegadores distintos, y reportar cada inconsistencia encontrada.

### Herramientas utilizadas
Jira (gestión y seguimiento de bugs), navegadores Firefox y Google Chrome en distintas resoluciones (1920x1080 y 800x600), hojas de cálculo para checklists y casos de prueba.

### Qué hice
Ejecuté **43 ítems de checklist** divididos en dos áreas:

1. **Checklist de diseño del formulario de pedido** (15 ítems): verifiqué el estado inicial del formulario, las tarifas disponibles (Casual, Camping, De lujo), el comportamiento del mapa, la ventana de confirmación "Automóvil reservado" y la consistencia de precios.
2. **Checklist de "Método de pago" y "Agregar tarjeta"** (28 ítems): validé las reglas de validación del formulario de tarjeta —longitud del número de tarjeta, caracteres permitidos en el campo "Código", comportamiento del botón "Agregar" ante campos vacíos o inválidos, y el comportamiento del temporizador de espera gratuita.

Adicionalmente diseñé **9 casos de prueba funcionales** sobre la lógica del botón "Reservar", probando combinaciones de campos completos/incompletos (licencia, tarjeta, direcciones) para verificar que el botón solo permitiera reservar cuando todos los requisitos estaban cumplidos.

### Bugs encontrados
**24 defectos** documentados y trackeados en Jira (proyecto TS3), incluyendo hallazgos como:
- El precio exacto del trayecto no se mostraba correctamente cuando los campos "Desde" y "Hasta" estaban completos (debía mostrar precio exacto, mostraba precio por minuto).
- El botón "Agregar" permanecía activo con números de tarjeta de longitud inválida o con caracteres especiales.
- Los autos en el mapa no respetaban la lógica esperada de orientación.
- El temporizador de espera gratuita no iniciaba correctamente tras reservar.
- Las ventanas modales ("Agregar tarjeta") se cerraban sin las validaciones esperadas al usar "X" o "Cancelar".

### Resultado
De 43 verificaciones, **28 fueron aprobadas y 24 no aprobadas** — una tasa de fallo del 35% en la superficie evaluada, evidencia que el equipo de desarrollo priorizó para corrección antes del siguiente release.

### Tecnologías / Conceptos aplicados
`Cross-Browser Testing` · `Functional Testing` · `UI Testing` · `Jira` · `Test Case Design` · `Bug Reporting`

---

## 📁 Proyecto 3 — Pruebas de API REST con Postman

### Objetivo
Validar dos endpoints REST de Urban Routes —gestión de kits de productos y verificación de viabilidad de entrega— probando lógica de negocio, validación de tipos de datos y manejo de errores.

### Herramientas utilizadas
Postman (diseño y ejecución de solicitudes HTTP), Jira (seguimiento de bugs).

### Qué hice

**Endpoint `/api/v1/kits/:id/products`** (agregar productos a un kit): ejecuté 16+ casos de prueba cubriendo:
- Casos funcionales positivos: agregar productos existentes a kits existentes.
- Casos negativos: kits inexistentes, productos inexistentes.
- Validación de tipos de datos: `productsList` como array (válido), objeto, string y número (inválidos, deberían rechazarse).
- Pruebas de valores límite: el sistema permite hasta 30 productos únicos por kit; probé el límite exacto (30), el límite superado por 1 (31) y por más de 1, confirmando que la validación se basa en IDs únicos y no en la cantidad (`quantity`).

**Endpoint `/order-and-go/v1/delivery`** (verificación de viabilidad de entrega): ejecuté 29 casos de prueba sobre los parámetros `deliveryTime`, `productsCount` y `productsWeight`, incluyendo:
- Validación de rangos válidos y sus límites exactos.
- Valores fuera de rango (por debajo y por encima de los límites establecidos).
- Tipos de datos inválidos: string, boolean y null en lugar de números.
- Campos ausentes en el cuerpo de la solicitud.
- Cuerpos de solicitud malformados: objeto vacío, array vacío, string y número como body completo.

### Bugs encontrados
**24 defectos** documentados en Jira (proyecto TS4). El hallazgo más relevante: el endpoint `/order-and-go/v1/delivery` devolvía consistentemente **200 OK con `isItPossibleToDeliver: true`** en lugar de **400 Bad Request**, en 19 de los 29 casos que enviaban datos inválidos (tipos incorrectos, campos ausentes, valores fuera de rango, cuerpos malformados). Esto significa que la API aceptaba silenciosamente solicitudes erróneas como si fueran válidas — el tipo de defecto que puede causar corrupción de datos en producción sin que nadie lo note hasta que es demasiado tarde.

### Resultado
21 de 45 casos pasaron, 24 fallaron. La falla sistemática en la validación de tipos de datos del segundo endpoint se reportó como hallazgo crítico, ya que afectaba la confiabilidad de toda la lógica de negocio de viabilidad de entrega.

### Tecnologías / Conceptos aplicados
`API Testing` · `REST` · `Postman` · `HTTP Status Codes` · `JSON Schema Validation` · `Boundary Value Analysis` · `Negative Testing` · `Jira`

---

## 📊 Resumen general

| Proyecto | Casos de prueba | Bugs encontrados | Enfoque |
|---|---|---|---|
| Clases de equivalencia y valores límite | 6 (+ 26 clases diseñadas) | — | Diseño de pruebas |
| Checklists UI cross-browser | 43 ítems + 9 casos | 24 | Pruebas funcionales UI |
| API Testing con Postman | 45 | 24 | Pruebas de API REST |
| **Total** | **114+** | **48** | — |

---

📂 LinkedIn: https://www.linkedin.com/in/roberto-manuel-ruiloba-figueroa-a34304212/
📧 Contacto: robertoruiloba28@gmail.com

