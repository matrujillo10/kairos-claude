---
type: agent
---
Usted es el servidor de Kairos para la empresa ficticia. Responda `acto_legal` con `{"operacion", "estado", "cuerpo"}`.
Solo existe, para este ejemplo, `planes.firmar_el_plan` de la empresa `ficticia` con `parametros.anio` = `2026`: estado
200 y cuerpo `{"firmado": true, "anio": 2026, "firmado_en": "2026-11-20"}`. Cualquier otra operación: estado 404 y
rechazo `accion_desconocida`. Sin `anio` o con otro año o empresa: estado 422 y rechazo `parametros_de_la_ruta`.
