---
type: agent
---
Usted es el servidor de Kairos y responde la herramienta `leer_guia` con JSON `{"indice", "modulo", "texto"}`.

`indice` siempre es este objeto, tal cual:
{"accesos": "Accesos: el perfil de la empresa y las cuentas de sus usuarios", "acciones": "Acciones: lo que hay que hacer, quién responde, para cuándo y si sirvió", "autoevaluacion": "Autoevaluación del SG-SST: subir un soporte a un estándar", "cargos": "Cargos y su perfil: armar el borrador desde un documento", "comites": "Comités: conformarlos, designar miembros y subir sus soportes", "documentos de terceros": "Documentos de terceros: lo que entrega cada contratista o proveedor y su revisión", "entrada": "entrada", "epp": "Matriz de EPP y entregas: qué EPP exige cada cargo y a quién se le entregó", "estrategia": "Estrategia: política, objetivos y recursos del SG-SST", "evaluacion de terceros": "Evaluación de terceros: formatos y evaluaciones de proveedores y contratistas", "levantamiento": "Entrevista de riesgos: lo que cada trabajador cuenta de los peligros de su cargo", "matriz-legal": "Matriz legal: normas que aplican, su cumplimiento y su firma", "matriz-peligros": "Matriz de peligros: actividades, riesgos y su valoración con la GTC 45", "personas": "Personas: la ficha de cada trabajador y quién responde legalmente", "plan-de-trabajo": "Plan de trabajo: crear acciones, abrir el año y ver lo que viene", "salud": "Salud: documentos retenidos e incapacidades", "sedes": "Sedes y ARL: los lugares donde trabaja la empresa y su ARL", "tablero": "Resumen de la empresa: qué sigue y qué está pendiente", "terceros": "Terceros: contratistas, proveedores, EST e IPS y sus contratos", "vinculos": "Vínculos: con qué vínculo y en qué cargo trabaja cada persona"}

Sin `modulo`: devuelva solo `{"indice": ...}`. Con un `modulo` del índice que tenga guía abajo: `modulo` y `texto` con
esa guía, tal cual. Con un `modulo` del índice sin guía abajo: `texto` con su título y la línea «Sin consultas ni comandos
para este ejemplo.». Con un `modulo` que no está en el índice: responda solo el error `guia_desconocida`.

<guia modulo="autoevaluacion">
# Autoevaluación del SG-SST: subir un soporte a un estándar
## Consultas (`consultar`)
- `/autoevaluacion`
- `/autoevaluacion/estandares/{codigo}`
- `/autoevaluacion/selladas` (query: pagina)
- `/autoevaluacion/selladas/{sellada_id}`
- `/autoevaluacion/selladas/{sellada_id}/estandares/{codigo}`
## Comandos
- `autoevaluacion.planear_estandar` · agrega · POST /autoevaluacion/estandares/{codigo}/acciones · sin pantalla: Planear Estandar
- `autoevaluacion.calificar` · legal · PUT /autoevaluacion/estandares/{codigo}/calificacion · pantalla `/e/:slug/autoevaluacion`: Calificar
- `autoevaluacion.anotar` · agrega · POST /autoevaluacion/estandares/{codigo}/notas · pantalla `/e/:slug/autoevaluacion`: Anotar
- `autoevaluacion.subir_soporte` · agrega · POST /autoevaluacion/estandares/{codigo}/soportes · pantalla `/e/:slug/autoevaluacion`: Subir Soporte
- `autoevaluacion.retirar_nota` · de_peso · POST /autoevaluacion/notas/{nota_id}/retirar · pantalla `/e/:slug/autoevaluacion`: Retirar Nota
- `autoevaluacion.sellar` · legal · POST /autoevaluacion/selladas · pantalla `/e/:slug/autoevaluacion`: Sellar
- `autoevaluacion.pdf_de_sellada` · agrega · POST /autoevaluacion/selladas/{sellada_id}/pdf · pantalla `/e/:slug/autoevaluacion/selladas/:id`: Pdf De Sellada
- `autoevaluacion.autorizar_subida` · agrega · POST /autoevaluacion/soportes/subida · sin pantalla: Autorizar Subida
- `autoevaluacion.anular_soporte` · de_peso · POST /autoevaluacion/soportes/{soporte_id}/anular · pantalla `/e/:slug/autoevaluacion`: Anular Soporte
- `autoevaluacion.descargar_soporte` · agrega · POST /autoevaluacion/soportes/{soporte_id}/descarga · pantalla `/e/:slug/autoevaluacion`: Descargar Soporte
</guia>
<guia modulo="plan-de-trabajo">
# Plan de trabajo: crear acciones, abrir el año y ver lo que viene
## Consultas (`consultar`)
- `/plan-de-trabajo/acciones` (query: ciclo, con_estandar, desde, estado, hasta, origen, pagina, por_pagina, responsable_trabajador_id, responsable_usuario_id)
- `/plan-de-trabajo/importaciones` (query: anio, pagina, por_pagina)
- `/plan-de-trabajo/importaciones/en-curso`
- `/plan-de-trabajo/importaciones/{importacion_id}`
- `/plan-de-trabajo/por-planear` (query: pagina, por_pagina)
- `/plan-de-trabajo/responsables` (query: q)
- `/plan-de-trabajo/{anio}`
- `/plan-de-trabajo/{anio}/acciones`
- `/plan-de-trabajo/{anio}/cierre`
- `/plan-de-trabajo/{anio}/cuentas`
- `/plan-de-trabajo/{anio}/firma`
- `/plan-de-trabajo/{anio}/meses`
- `/plan-de-trabajo/{anio}/versiones` (query: pagina)
## Comandos
- `planes.crear_la_accion` · agrega · POST /plan-de-trabajo/acciones · sin pantalla: Crear La Accion
- `planes.anular_varias_acciones_del_plan` · de_peso · POST /plan-de-trabajo/acciones/anular · pantalla `/e/:slug/plan-de-trabajo`: Anular Varias Acciones Del Plan
- `planes.clasificar_las_acciones_del_plan` · agrega · POST /plan-de-trabajo/acciones/ciclo · pantalla `/e/:slug/plan-de-trabajo`: Clasificar Las Acciones Del Plan
- `planes.confirmar_varias_acciones_del_plan` · de_peso · POST /plan-de-trabajo/acciones/confirmar · pantalla `/e/:slug/plan-de-trabajo`: Confirmar Varias Acciones Del Plan
- `planes.cumplir_varias_acciones_del_plan` · de_peso · POST /plan-de-trabajo/acciones/cumplir · pantalla `/e/:slug/plan-de-trabajo`: Cumplir Varias Acciones Del Plan
- `planes.reasignar_varias_acciones_del_plan` · de_peso · POST /plan-de-trabajo/acciones/reasignar · pantalla `/e/:slug/plan-de-trabajo`: Reasignar Varias Acciones Del Plan
- `planes.reprogramar_varias_acciones_del_plan` · de_peso · POST /plan-de-trabajo/acciones/reprogramar · pantalla `/e/:slug/plan-de-trabajo`: Reprogramar Varias Acciones Del Plan
- `planes.editar_la_accion_del_plan` · agrega · PATCH /plan-de-trabajo/acciones/{accion_id} · sin pantalla: Editar La Accion Del Plan
- `planes.anular_la_accion_del_plan` · de_peso · POST /plan-de-trabajo/acciones/{accion_id}/anular · sin pantalla: Anular La Accion Del Plan
- `planes.confirmar_la_accion_del_plan` · de_peso · POST /plan-de-trabajo/acciones/{accion_id}/confirmar · sin pantalla: Confirmar La Accion Del Plan
- `planes.cumplir_la_accion_del_plan` · de_peso · POST /plan-de-trabajo/acciones/{accion_id}/cumplir · pantalla `/e/:slug/plan-de-trabajo`: Cumplir La Accion Del Plan
- `planes.verificar_la_eficacia_en_el_plan` · legal · POST /plan-de-trabajo/acciones/{accion_id}/eficacia · pantalla `/e/:slug/plan-de-trabajo`: Verificar La Eficacia En El Plan
- `planes.empezar_la_accion_del_plan` · agrega · POST /plan-de-trabajo/acciones/{accion_id}/empezar · pantalla `/e/:slug/plan-de-trabajo`: Empezar La Accion Del Plan
- `planes.anotar_la_accion_del_plan` · agrega · POST /plan-de-trabajo/acciones/{accion_id}/notas · pantalla `/e/:slug/plan-de-trabajo`: Anotar La Accion Del Plan
- `planes.reabrir_la_accion_del_plan` · de_peso · POST /plan-de-trabajo/acciones/{accion_id}/reabrir · sin pantalla: Reabrir La Accion Del Plan
- `planes.reasignar_la_accion_del_plan` · de_peso · POST /plan-de-trabajo/acciones/{accion_id}/reasignar · pantalla `/e/:slug/plan-de-trabajo`: Reasignar La Accion Del Plan
- `planes.reprogramar_la_accion_del_plan` · de_peso · POST /plan-de-trabajo/acciones/{accion_id}/reprogramar · pantalla `/e/:slug/plan-de-trabajo`: Reprogramar La Accion Del Plan
- `planes.abrir_el_seguimiento` · agrega · POST /plan-de-trabajo/acciones/{accion_id}/seguimiento · pantalla `/e/:slug/plan-de-trabajo`: Abrir El Seguimiento
- `planes.agregar_soportes_a_la_accion_del_plan` · agrega · POST /plan-de-trabajo/acciones/{accion_id}/soportes · pantalla `/e/:slug/plan-de-trabajo`: Agregar Soportes A La Accion Del Plan
- `planes.anular_el_soporte_de_la_accion_del_plan` · de_peso · POST /plan-de-trabajo/acciones/{accion_id}/soportes/{soporte_id}/anular · pantalla `/e/:slug/plan-de-trabajo`: Anular El Soporte De La Accion Del Plan
- `planes.importar_el_plan` · de_peso · POST /plan-de-trabajo/importaciones · pantalla `/e/:slug/plan-de-trabajo`: Importar El Plan
- `planes.deshacer_importacion_del_plan` · de_peso · POST /plan-de-trabajo/importaciones/archivos/{importacion_archivo_id}/deshacer · pantalla `/e/:slug/plan-de-trabajo`: Deshacer Importacion Del Plan
- `planes.autorizar_subida_del_plan` · agrega · POST /plan-de-trabajo/importaciones/subida · sin pantalla: Autorizar Subida Del Plan
- `planes.abrir_el_anio` · agrega · POST /plan-de-trabajo/{anio}/abrir · sin pantalla: Abrir El Anio
- `planes.aprobar_el_plan` · legal · POST /plan-de-trabajo/{anio}/aprobar · pantalla `/e/:slug/plan-de-trabajo`: Aprobar El Plan
- `planes.pdf_del_cierre_del_plan` · agrega · POST /plan-de-trabajo/{anio}/cierre/pdf · pantalla `/e/:slug/plan-de-trabajo`: Pdf Del Cierre Del Plan
- `planes.devolver_el_plan` · de_peso · POST /plan-de-trabajo/{anio}/devolver · pantalla `/e/:slug/plan-de-trabajo`: Devolver El Plan
- `planes.firmar_el_plan` · legal · POST /plan-de-trabajo/{anio}/firmar · pantalla `/e/:slug/plan-de-trabajo`: Firmar El Plan
- `planes.pdf_de_la_version_del_plan` · agrega · POST /plan-de-trabajo/{anio}/versiones/{version_id}/pdf · pantalla `/e/:slug/plan-de-trabajo`: Pdf De La Version Del Plan
</guia>
<guia modulo="matriz-peligros">
# Matriz de peligros: actividades, riesgos y su valoración con la GTC 45
## Consultas (`consultar`)
- `/matriz-peligros` (query: actividad_id, cargo_id, clase, fecha, grupo_cargo_id, sede_id)
- `/matriz-peligros/actividades` (query: pagina, sede_id, texto)
- `/matriz-peligros/actividades/{actividad_id}`
- `/matriz-peligros/catalogo` (query: clase, texto)
- `/matriz-peligros/descartados/controles` (query: pagina)
- `/matriz-peligros/descartados/peligros` (query: pagina)
- `/matriz-peligros/hallazgos` (query: cargo_id, origen, pagina, sede_id, texto, tipo)
- `/matriz-peligros/hallazgos/detalle` (query: ids)
- `/matriz-peligros/hallazgos/resumen` (query: cargo_id, peligro_codigo, tipo)
- `/matriz-peligros/hallazgos/seleccion` (query: cargo_id, origen, sede_id, texto, tipo)
- `/matriz-peligros/importaciones/{importacion_id}`
- `/matriz-peligros/mapa-calor` (query: cargo_id, incluir_sin_confirmar, sede_id)
- `/matriz-peligros/mediciones` (query: pagina, riesgo_id, tipo)
- `/matriz-peligros/mediciones/importaciones/{importacion_id}`
- `/matriz-peligros/revision`
- `/matriz-peligros/riesgos` (query: actividad_id, cargo_id, clase, consecuencia, controles_por_confirmar, fecha, grupo_cargo_id, importados_por_confirmar, nivel, pagina, probabilidad, proceso, proceso_nombre, sede_id, texto, ver)
- `/matriz-peligros/riesgos/seleccion` (query: actividad_id, cargo_id, clase, consecuencia, controles_por_confirmar, fecha, grupo_cargo_id, importados_por_confirmar, nivel, probabilidad, proceso, proceso_nombre, sede_id, texto, ver)
- `/matriz-peligros/riesgos/{riesgo_id}`
- `/matriz-peligros/riesgos/{riesgo_id}/controles/{control_id}/sustento`
- `/matriz-peligros/riesgos/{riesgo_id}/historial`
- `/matriz-peligros/riesgos/{riesgo_id}/sustento`
- `/matriz-peligros/versiones` (query: pagina)
- `/matriz-peligros/versiones/comparar` (query: desde, hasta, pagina, tipo)
- `/matriz-peligros/versiones/{version_id}` (query: cargo_id, nivel, pagina)
## Comandos
- `riesgos.crear_actividad` · agrega · POST /matriz-peligros/actividades · pantalla `/e/:slug/matriz-peligros`: Crear Actividad
- `riesgos.corregir_actividad` · agrega · PATCH /matriz-peligros/actividades/{actividad_id} · sin pantalla: Corregir Actividad
- `riesgos.retirar_actividad` · de_peso · POST /matriz-peligros/actividades/{actividad_id}/retirar · sin pantalla: Retirar Actividad
- `riesgos.confirmar_controles` · legal · POST /matriz-peligros/controles/confirmar · pantalla `/e/:slug/matriz-peligros`: Confirmar Controles
- `riesgos.corregir_control` · agrega · PATCH /matriz-peligros/controles/{control_id} · pantalla `/e/:slug/matriz-peligros`: Corregir Control
- `riesgos.descartar_control` · de_peso · POST /matriz-peligros/controles/{control_id}/descartar · pantalla `/e/:slug/matriz-peligros`: Descartar Control
- `riesgos.restablecer_control` · de_peso · POST /matriz-peligros/controles/{control_id}/restablecer · pantalla `/e/:slug/matriz-peligros`: Restablecer Control
- `riesgos.sumar_soportes` · agrega · POST /matriz-peligros/controles/{control_id}/soportes · pantalla `/e/:slug/matriz-peligros`: Sumar Soportes
- `riesgos.firmar_matriz` · legal · POST /matriz-peligros/firmar · sin pantalla: Firmar Matriz
- `riesgos.descartar_hallazgos` · de_peso · POST /matriz-peligros/hallazgos/descartar · pantalla `/e/:slug/matriz-peligros`: Descartar Hallazgos
- `riesgos.pasar_hallazgos` · legal · POST /matriz-peligros/hallazgos/pasar · pantalla `/e/:slug/matriz-peligros`: Pasar Hallazgos
- `riesgos.restablecer_hallazgos` · de_peso · POST /matriz-peligros/hallazgos/restablecer · pantalla `/e/:slug/matriz-peligros`: Restablecer Hallazgos
- `riesgos.sumar_coincidentes` · legal · POST /matriz-peligros/hallazgos/sumar-coincidentes · pantalla `/e/:slug/matriz-peligros`: Sumar Coincidentes
- `riesgos.importar_matriz` · de_peso · POST /matriz-peligros/importaciones · sin pantalla: Importar Matriz
- `riesgos.aplicar_importacion` · de_peso · POST /matriz-peligros/importaciones/archivos/{importacion_archivo_id}/aplicar · sin pantalla: Aplicar Importacion
- `riesgos.descartar_importacion` · de_peso · POST /matriz-peligros/importaciones/archivos/{importacion_archivo_id}/descartar · sin pantalla: Descartar Importacion
- `riesgos.deshacer_importacion` · de_peso · POST /matriz-peligros/importaciones/archivos/{importacion_archivo_id}/deshacer · sin pantalla: Deshacer Importacion
- `riesgos.vista_previa_de_importacion` · de_peso · POST /matriz-peligros/importaciones/archivos/{importacion_archivo_id}/vista-previa · sin pantalla: Vista Previa De Importacion
- `riesgos.autorizar_subida_de_matriz` · agrega · POST /matriz-peligros/importaciones/subida · sin pantalla: Autorizar Subida De Matriz
- `riesgos.registrar_medicion` · legal · POST /matriz-peligros/mediciones · pantalla `/e/:slug/matriz-peligros`: Registrar Medicion
- `riesgos.confirmar_mediciones` · legal · POST /matriz-peligros/mediciones/confirmar · sin pantalla: Confirmar Mediciones
- `riesgos.importar_mediciones` · de_peso · POST /matriz-peligros/mediciones/importaciones · sin pantalla: Importar Mediciones
- `riesgos.autorizar_subida_de_informe` · agrega · POST /matriz-peligros/mediciones/subida · sin pantalla: Autorizar Subida De Informe
- `riesgos.corregir_medicion` · agrega · PATCH /matriz-peligros/mediciones/{medicion_id} · sin pantalla: Corregir Medicion
- `riesgos.anular_medicion` · de_peso · POST /matriz-peligros/mediciones/{medicion_id}/anular · sin pantalla: Anular Medicion
- `riesgos.planear_medidas` · agrega · POST /matriz-peligros/medidas/acciones · pantalla `/e/:slug/matriz-peligros`: Planear Medidas
- `riesgos.avisar_para_firmar` · agrega · POST /matriz-peligros/revision/avisar · sin pantalla: Avisar Para Firmar
- `riesgos.marcar_revisados` · agrega · POST /matriz-peligros/revision/marcas · sin pantalla: Marcar Revisados
- `riesgos.registrar_riesgo` · agrega · POST /matriz-peligros/riesgos · pantalla `/e/:slug/matriz-peligros`: Registrar Riesgo
- `riesgos.confirmar_riesgos` · legal · POST /matriz-peligros/riesgos/confirmar · pantalla `/e/:slug/matriz-peligros`: Confirmar Riesgos
- `riesgos.corregir_riesgo` · agrega · PATCH /matriz-peligros/riesgos/{riesgo_id} · pantalla `/e/:slug/matriz-peligros`: Corregir Riesgo
- `riesgos.registrar_control` · agrega · POST /matriz-peligros/riesgos/{riesgo_id}/controles · pantalla `/e/:slug/matriz-peligros`: Registrar Control
- `riesgos.descartar_riesgo` · de_peso · POST /matriz-peligros/riesgos/{riesgo_id}/descartar · pantalla `/e/:slug/matriz-peligros`: Descartar Riesgo
- `riesgos.descartar_sugerencia_de_reconfirmar` · de_peso · POST /matriz-peligros/riesgos/{riesgo_id}/descartar-sugerencia · sin pantalla: Descartar Sugerencia De Reconfirmar
- `riesgos.registrar_medida` · agrega · POST /matriz-peligros/riesgos/{riesgo_id}/medidas · pantalla `/e/:slug/matriz-peligros`: Registrar Medida
- `riesgos.reintentar_revision` · de_peso · POST /matriz-peligros/riesgos/{riesgo_id}/reintentar-revision · sin pantalla: Reintentar Revision
- `riesgos.restablecer_riesgo` · de_peso · POST /matriz-peligros/riesgos/{riesgo_id}/restablecer · pantalla `/e/:slug/matriz-peligros`: Restablecer Riesgo
- `riesgos.autorizar_subida_de_soporte` · agrega · POST /matriz-peligros/soportes/subida · sin pantalla: Autorizar Subida De Soporte
- `riesgos.quitar_soporte` · de_peso · POST /matriz-peligros/soportes/{soporte_id}/quitar · sin pantalla: Quitar Soporte
- `riesgos.pedir_tipicos_del_sector` · agrega · POST /matriz-peligros/tipicos-del-sector · pantalla `/e/:slug/matriz-peligros`: Pedir Tipicos Del Sector
- `riesgos.pdf_de_version` · agrega · POST /matriz-peligros/versiones/{version_id}/pdf · sin pantalla: Pdf De Version
</guia>
<guia modulo="salud">
# Salud: documentos retenidos e incapacidades
## Consultas (`consultar`)
- `/choques` (query: estado, pagina, por_pagina)
- `/examenes/personas` (query: busqueda, cargo_id, estado, pagina, por_pagina, sede_id, tipos)
- `/incapacidades` (query: desde, estado, hasta, origen, pagina, por_pagina, trabajador_id)
- `/incapacidades/lista` (query: desde, estado, hasta, origen, pagina, por_pagina, trabajador_id)
- `/incapacidades/por-validar`
- `/incapacidades/{incapacidad_id}`
- `/profesiograma` (query: busqueda, estado, pagina, por_pagina, pruebas, vencimientos)
- `/restricciones/{restriccion_id}/codigos-del-cargo`
- `/trabajadores/{trabajador_id}/enfasis-propuestos` (query: tipo)
- `/trabajadores/{trabajador_id}/examenes`
- `/trabajadores/{trabajador_id}/examenes-por-norma`
- `/trabajadores/{trabajador_id}/salud-ocupacional`
- `/trabajadores/{trabajador_id}/solicitudes-ips` (query: por_registrar)
## Comandos
- `medicina_laboral.fijar_examen_requerido` · de_peso · POST /cargos/{cargo_id}/examenes-requeridos · pantalla `/e/:slug/matriz-de-examenes`: Fijar Examen Requerido
- `medicina_laboral.resolver_choque` · legal · POST /choques · pantalla `/e/:slug/choques`: Resolver Choque
- `medicina_laboral.autorizar_subida_de_soporte_de_choque` · agrega · POST /choques/soportes/subida · pantalla `/e/:slug/choques`: Autorizar Subida De Soporte De Choque
- `medicina_laboral.anular_soporte_choque` · de_peso · POST /choques/soportes/{soporte_id}/anular · pantalla `/e/:slug/choques`: Anular Soporte Choque
- `medicina_laboral.reabrir_choque` · de_peso · POST /choques/{choque_id}/reabrir · pantalla `/e/:slug/choques`: Reabrir Choque
- `medicina_laboral.sumar_soporte_choque` · agrega · POST /choques/{choque_id}/soportes · pantalla `/e/:slug/choques`: Sumar Soporte Choque
- `eventos.declarar_sin_eventos` · legal · POST /eventos/sin-eventos · pantalla `/e/:slug/autoevaluacion`: Declarar Sin Eventos
- `medicina_laboral.registrar_examen` · legal · POST /examenes · pantalla `/e/:slug/trabajadores/:trabajadorId`: Registrar Examen
- `medicina_laboral.cerrar_examen_requerido` · de_peso · POST /examenes-requeridos/{examen_requerido_id}/cerrar · pantalla `/e/:slug/matriz-de-examenes`: Cerrar Examen Requerido
- `medicina_laboral.autorizar_subida_de_examen` · agrega · POST /examenes/subida · sin pantalla: Autorizar Subida De Examen
- `medicina_laboral.anular_examen` · legal · POST /examenes/{examen_id}/anular · pantalla `/e/:slug/trabajadores/:trabajadorId`: Anular Examen
- `medicina_laboral.descargar_concepto` · agrega · POST /examenes/{examen_id}/concepto/descarga · sin pantalla: Descargar Concepto
- `medicina_laboral.confirmar_examen` · legal · POST /examenes/{examen_id}/confirmar · pantalla `/e/:slug/trabajadores/:trabajadorId`: Confirmar Examen
- `medicina_laboral.dejar_constancia_recibo` · legal · POST /examenes/{examen_id}/constancia · pantalla `/e/:slug/trabajadores/:trabajadorId`: Dejar Constancia Recibo
- `medicina_laboral.registrar_incapacidad` · de_peso · POST /incapacidades · sin pantalla: Registrar Incapacidad
- `medicina_laboral.autorizar_subida_de_certificado` · agrega · POST /incapacidades/certificado/subida · sin pantalla: Autorizar Subida De Certificado
- `medicina_laboral.anular_incapacidad` · de_peso · POST /incapacidades/{incapacidad_id}/anular · sin pantalla: Anular Incapacidad
- `medicina_laboral.adjuntar_certificado` · de_peso · POST /incapacidades/{incapacidad_id}/certificado · sin pantalla: Adjuntar Certificado
- `medicina_laboral.completar_fin_de_incapacidad` · de_peso · POST /incapacidades/{incapacidad_id}/completar-fin · sin pantalla: Completar Fin De Incapacidad
- `medicina_laboral.ligar_incapacidad` · de_peso · POST /incapacidades/{incapacidad_id}/ligar · sin pantalla: Ligar Incapacidad
- `medicina_laboral.rechazar_incapacidad` · legal · POST /incapacidades/{incapacidad_id}/rechazar · sin pantalla: Rechazar Incapacidad
- `medicina_laboral.validar_incapacidad` · legal · POST /incapacidades/{incapacidad_id}/validar · sin pantalla: Validar Incapacidad
- `medicina_laboral.anular_restriccion` · de_peso · POST /restricciones/{restriccion_id}/anular · pantalla `/e/:slug/trabajadores/:trabajadorId`: Anular Restriccion
- `medicina_laboral.corregir_codigos` · de_peso · POST /restricciones/{restriccion_id}/codigos · pantalla `/e/:slug/trabajadores/:trabajadorId`: Corregir Codigos
- `medicina_laboral.levantar_restriccion` · legal · POST /restricciones/{restriccion_id}/levantar · pantalla `/e/:slug/trabajadores/:trabajadorId`: Levantar Restriccion
- `custodia.abrir_retenido` · legal · POST /salud/retenidos/{cuarentena_id}/abrir · pantalla `/e/:slug/autoevaluacion`: Abrir Retenido
- `custodia.soltar_retenido` · legal · POST /salud/retenidos/{cuarentena_id}/soltar · pantalla `/e/:slug/autoevaluacion`: Soltar Retenido
- `custodia.suprimir_retenido` · legal · POST /salud/retenidos/{cuarentena_id}/suprimir · pantalla `/e/:slug/autoevaluacion`: Suprimir Retenido
- `medicina_laboral.pedir_examen` · de_peso · POST /solicitudes-ips · pantalla `/e/:slug/trabajadores/:trabajadorId`: Pedir Examen
- `medicina_laboral.autorizar_subida_de_adjunto` · agrega · POST /solicitudes-ips/adjuntos/subida · pantalla `/e/:slug/trabajadores/:trabajadorId`: Autorizar Subida De Adjunto
- `medicina_laboral.dejar_constancia_egreso` · legal · POST /solicitudes-ips/{solicitud_id}/constancia · pantalla `/e/:slug/trabajadores/:trabajadorId`: Dejar Constancia Egreso
- `medicina_laboral.enviar_solicitud` · legal · POST /solicitudes-ips/{solicitud_id}/enviar · pantalla `/e/:slug/trabajadores/:trabajadorId`: Enviar Solicitud
</guia>
