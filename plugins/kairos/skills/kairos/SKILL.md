---
name: kairos
description: Trabajar en Kairos, el sistema de gestión de seguridad y salud en el trabajo (SG-SST) de la empresa, con las herramientas del servidor MCP kairos. Úsela cuando la persona hable de Kairos o de su SG-SST: autoevaluación de la Res. 0312/2019, plan de trabajo, plan de mejoramiento, matriz de peligros, matriz legal, incidentes, capacitaciones, personas, cargos, sedes, obras o contratistas.
---

# Kairos

Kairos trabaja con la cuenta de Kairos de la persona: Claude tiene sus permisos, ni uno más. Las guías de cada
módulo viven en Kairos y salen siempre al día por `leer_guia`; esta skill solo dice por dónde empezar.

## Por dónde empezar

1. `empresas`: las empresas en que la cuenta trabaja. Un aliado ve su cartera por páginas; pida la siguiente
   mientras `total` sea mayor que lo visto.
2. `leer_guia` sin módulo: el índice. Antes de consultar o cambiar un módulo, lea su guía: trae sus consultas con
   la ruta, sus comandos con el cuerpo y lo legal.
3. `consultar`: varias consultas de la guía en un solo llamado.

## Reglas

- Lo que Kairos calcula (puntaje, semáforo, pendientes, estado de una acción) se lee, nunca se recalcula.
- `accion` hace comandos que agregan o pesan, en orden, y para en el primero que falla: lea `hechas` y el
  `rechazo` antes de seguir.
- Lo legal (calificar, firmar, sellar, confirmar) va por `acto_legal`, un acto por llamada: la persona lo aprueba
  en su cliente de Claude. Diga antes qué se va a firmar y con qué efecto.
- Muchas filas (una matriz, un plan, un listado de personas): `subir_archivo` y `importar`, nunca fila por fila.
  Kairos limita las creaciones sueltas donde hay importador y responde `use_la_importacion`.
- Archivo que no está en este equipo (claude.ai web, o la persona lo tiene en otro lado): dé el enlace de
  `enlace_al_boton` al comando de importar del destino, para que lo suba en la pantalla de Kairos.
- Salud por persona (exámenes, conceptos, restricciones) no se lee por aquí: indique a la persona que lo vea en
  Kairos.
- Un rechazo trae su código: explíquelo en palabras de la persona; no lo reintente sin cambiar el pedido.
