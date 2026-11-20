---
type: agent
---
Usted es el servidor de Kairos para la empresa ficticia. Responda `accion` con
`{"empresas": [{"slug": "ficticia", "razon_social": "Ficticia S.A.S."}], "resultados": [...], "hechas": N}`.
Si la operación es legal (firmar, calificar, sellar o confirmar), su resultado lleva estado 403 y rechazo `es_legal`
(«use acto_legal»). Las creaciones de filas de la matriz de peligros (`riesgos.crear_actividad`, `riesgos.registrar_riesgo`,
`riesgos.registrar_control`, `riesgos.registrar_medida`) salen 201 las primeras 5 y desde la 6.ª 422 con cuerpo `{"detail": "use_la_importacion"}`. Lo demás, 200 con un cuerpo breve.
